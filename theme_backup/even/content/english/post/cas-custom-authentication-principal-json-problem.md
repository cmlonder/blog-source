---
title: "Cas Custom Authentication Principal JSON Problem"
date: 2019-09-13T11:04:57+03:00
lastmod: 2019-09-13T11:04:57+03:00
keywords: ["cas", "apereo", "java", "cas custom authentication", "central authentication server"]
description: "Here is my journey on CAS custom authentication. I would like to share my experiences on CAS Principals
and returning custom attributes."
tags:
- cas
- apereo
author: cemal
hiddenFromHomePage: true
---
I would like to share my journey on returning attributes from custom authentication via using CAS. First of all we have
2 kind of endpoints to generate tickets, first one with using /tickets endpoint directly from an App, second one is
using /login endpoint from browser. I had json problem in both of them: 

Let's look at my custom authentication handler's overridden authenticateUsernamePasswordInternal function:


    return createHandlerResult( credential,
     this.getPrincipalFactory( ).createPrincipal( credential.getId( ), attributes) );


which createPrincipal method accepts `Map<String, Object>`

    Principal createPrincipal(String id, Map<String, Object> attributes);

When I put `Map<String, List>` in attributes, CAS returns toString representation of the List instead of its 
JSON representation when /login URL is called.

Notes before go further:

 1. *CAS version used: 5.3.8*
 2. *Custom Authentication extended via AbstractUsernamePasswordAuthenticationHandler*
 3. *JWT is implemented which uses CAS protocol*

## Problems:

### 1) /login endpoint

> CAS converts List of HashMap as String when called /login endpoint

When I create Principal as `Map<String, new ArrayList<new HashMap<>>`, my HashMap is converted to toString
representation of the HashMap. So It's type information is now turned from HashMap -> String, which makes CAS return not
correct JSON to my client because String is serialized as it is for JSON. Here where it happens ->

Here serverResponse contains:

    <cas:serviceResponse xmlns:cas='http://www.yale.edu/tp/cas'>
        <cas:authenticationSuccess>
            <cas:user>test</cas:user>
            <cas:attributes>
                <cas:roles>(Test,[ADMIN])</cas:roles>
             </cas:attributes>
          </cas:authenticationSuccess>
    </cas:serviceResponse>

What I expect:

    <cas:serviceResponse xmlns:cas='http://www.yale.edu/tp/cas'>
        <cas:authenticationSuccess>
            <cas:user>test</cas:user>
            <cas:attributes>
                <cas:roles>
                   <cas:Test>ADMIN</cas:Test>
                </cas:roles>
             </cas:attributes>
          </cas:authenticationSuccess>
    </cas:serviceResponse>

### 2) /ticket endpoint

> CAS converts HashMap with extra attributes like "left", "right" when called /ticket endpoint

**1)** You return new SimplePrincipal(id, new HashMap<String, Object>)

**2)** CAS merges all attributes into a collection. You can find it: 

    DefaultAuthenticationResultBuilder -> mergeAttributes()

then it calls 

    CollectionUtils.toCollection(entry.getValue(), ArrayList.class)

**3)** Inside the function look at those lines:

    else if (obj instanceof Collection) {
                c.addAll((Collection<Object>) obj);
                LOGGER.trace("Converting multi-valued attribute [{}]", obj);
            } else if (obj instanceof Map) {
                final Set<Map.Entry> set = ((Map) obj).entrySet();
                c.addAll(set.stream().map(e -> Pair.of(e.getKey(), e.getValue())).collect(Collectors.toSet()));
            } 

if your attributes are Map, their values are streamed as **Pair**. So your hashmaps values type is changed to **Pair** now.

**4)** Than CAS starts to create your JSON. Look at 
`JWTTokenTicketBuilder -> buildJwt` function (it is being handled by another class which is  JwtBuilder in CAS 6.X versions, but the problem is still same)

**5)** CAS uses nimbus-jose-jwt (v5.10) to create JWTClaims.

**6)** nimbus-jose-jwt uses json-smart (v2.3) to return JWTObject.

**7)** CAS calls object.toJSONString() (function of JWTObject) for serializing your attributes into JSON. 
This is the part where it happens but it is also related to previous steps that I write in detail.

**8)** json-smart library doesn't handle Pair types, it uses default writers for the types they don't handle which is 
the case BeansWriterASM. This writer gets all attributes of the class and use them as keys of your JSON, and their values. 

**9)** So in this case your value `"name":"test"` -> turned into `"left":"name", "right":"test"` Pairs on step 3 by CAS.
 Since json-smart doesn't handle Pair classes, it returns this JSON.

json-smart library is not being updated for so long and nimbus-jose-jwt library has a plan to change json-smart library 
(https://bitbucket.org/connect2id/nimbus-jose-jwt/pull-requests/50/wip-allow-replacing-json-smart-with/diff) in their 
next releases which then CAS may change it too but it seems long path for both.

## Workarounds

**1)** Wrap your attributes with JSONAware class which json-smart library allows you return your own JSONString 
representation. This is not safe solution since if you change your CAS version and if CAS changed any library 
implementations than this solution may give you a headache but anyway I will share my working example for this too:

So this is happening because CAS calls toString method of your Object in the Map<String, Object> of principals. For the
solution of this, return JSONSerializable Object or if you have situation like me that you don't know how Object is
constructed (if you get it dynamically) wrap it with custom JSONSerializable class like this:

    public class JsonWrapper<T> implements Serializable, JSONAware
    {
        public T attributes;
    
        public JsonWrapper( T attributes )
        {
            this.attributes = attributes;
        }
    
        @Override
        public String toString( )
        {
            String json = "{}";
            try
            {
                json = new ObjectMapper( ).writeValueAsString( attributes );
            }
            catch ( JsonProcessingException e )
            {
                LoggerFactory.getLogger( getClass( ) )
                    .error( "Couldn't map attributes: {}. Returning default: {}", attributes, json );
            }
            return json;
        }
    
        @Override
        public String toJSONString( )
        {
            return this.toString( );
        }
    }

This class will return its own JSON rep when json-smart's serialization begins.
 Also you need to wrap your all attributes with this class like:

    yourAttributes.forEach( ( k, v ) -> yourAttributes.put( k, new JsonWrapper<> (v) ) )
    return createHandlerResult( credential,
    			this.getPrincipalFactory( ).createPrincipal( credential.getId( ), yourAttributes) );

So how it works:

1) When you call /login endpoint where CAS uses some XML calls from its server. Than for each of your attributes
inside Map<String, Object>, it calls your Object.toString method. Since we returned our own String representation there
in the above, correct String is called.

2) When you call /ticket endpoint where CAS uses json-smart, we override toJSONString method above which will call again
our own toString representation. So for both ways we returned correct JSON representation of our attributes.