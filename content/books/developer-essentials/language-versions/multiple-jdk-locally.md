---
title: Multiple JDK Locally
summary: Learn how to install and manage multiple jdk versions in Mac OS
type: book
weight: 10
date: "2021-01-17T00:00:00Z"
lastMod: "2021-01-17T00:00:00Z"
---
In this tutorial we are going to install and configure Jenv to manage multiple JDK versions in Mac OS. 

At the end you will;
* easily change your global java version 
* use different java version rather than global java version in any folder
* configure the maven so it also uses the local/global version you set

## Prerequisite
* Homebrew

## Install Multiple JDK
Before we install the Jenv, we need to have multiple JDK versions installed in our local.

* You can search for available openjdk with:
```
brew search openjdk
```

```
==> Formulae
openjdk ✔                                              openjdk@11 ✔                                           openjdk@8
==> Casks
adoptopenjdk                     adoptopenjdk11-openj9            adoptopenjdk12-openj9-large      adoptopenjdk14-openj9            adoptopenjdk15-openj9-large
adoptopenjdk-jre                 adoptopenjdk11-openj9-jre        adoptopenjdk13 ✔                 adoptopenjdk14-openj9-jre        adoptopenjdk8
adoptopenjdk-openj9              adoptopenjdk11-openj9-jre-large  adoptopenjdk13-jre               adoptopenjdk14-openj9-jre-large  adoptopenjdk8
adoptopenjdk-openj9-jre          adoptopenjdk11-openj9-large      adoptopenjdk13-openj9            adoptopenjdk14-openj9-large      adoptopenjdk8-jre
adoptopenjdk-openj9-jre-large    adoptopenjdk12                   adoptopenjdk13-openj9-jre        adoptopenjdk15                   adoptopenjdk8-openj9
adoptopenjdk-openj9-large        adoptopenjdk12-jre               adoptopenjdk13-openj9-jre-large  adoptopenjdk15-jre               adoptopenjdk8-openj9-jre
adoptopenjdk10                   adoptopenjdk12-openj9            adoptopenjdk13-openj9-large      adoptopenjdk15-openj9            adoptopenjdk8-openj9-jre-large
adoptopenjdk11                   adoptopenjdk12-openj9-jre        adoptopenjdk14                   adoptopenjdk15-openj9-jre        adoptopenjdk8-openj9-large
adoptopenjdk11-jre               adoptopenjdk12-openj9-jre-large  adoptopenjdk14-jre               adoptopenjdk15-openj9-jre-large  adoptopenjdk9
```

* Install a chosen jdk (openjdk@11 in this case)
```
brew install openjdk@11
```

* Make symlink link to jdk 11 location (brew also will guide you if you read it's output in terminal)
```
sudo ln -sfn /usr/local/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-11.jdk
```

* Install an another JDK (openjdk@15 in this case)
```
brew install openjdk@15
```

* Make symlink link to jdk 15 location
```
sudo ln -sfn /usr/local/opt/openjdk@15/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-15.jdk
```

## Install Jenv
* Install Jenv using homebrew
```
brew install jenv
```

* Init jenv to set JAVA_HOME for you. If you run ```echo $JAVA_HOME``` you will get no result
(or maybe incorrect result if you have java before). We should configure jenv first, to get some help run:

```
jenv doctor
```

which will give you the command you should run to configure jenv some required settings to your bash profile. Below is mine,
**check your terminal output** for yours:

```
echo eval "$(jenv init -)" >> /Users/cemal.onder/.zshrc
```

## Add Java Homes to Jenv
We should now show our installed JDK home locations to jenv. For this either use your installed url's in previous steps or 
type in your terminal `/Library/Java/JavaVirtualMachines/` and hit the **tab** to list available jdk versions. And use full 
path as ` /Library/Java/JavaVirtualMachines/${YOUR_INSTALLED_VERSION/Contents/Home`

* Add JDK 11 home link to Jenv
```
jenv add /Library/Java/JavaVirtualMachines/openjdk.jdk/Contents/Home
```

* Add JDK 15 one also to Jenv
```
jenv add /Library/Java/JavaVirtualMachines/openjdk-15.jdk/Contents/Home
```

* Check your java versions in Jenv
```
jenv versions
```

```
      system
    * 11 (set by /Users/cemal.onder/.jenv/version)
      11.0
      11.0.9
      15
      15.0
      15.0.1
      openjdk64-11.0.9
      openjdk64-15.0.1
```

Point (*) next to **11** shows my global JDK version.

## Change global JDK Version
Now we can set a global JDK in our local using jenv which will change $JAVA_HOME version.

* First check your java version
```
cemal.onder@C02DM1Y9MD6R ~ % java --version
openjdk 15.0.1 2020-10-20
OpenJDK Runtime Environment (build 15.0.1+9)
OpenJDK 64-Bit Server VM (build 15.0.1+9, mixed mode, sharing)
```

* Change global java version
```
jenv global 11
```

* Now check java version again which is changed from 15 to 11
```
    cemal.onder@C02DM1Y9MD6R ~ % java --version
    openjdk 11.0.9 2020-10-20
    OpenJDK Runtime Environment (build 11.0.9+11)
    OpenJDK 64-Bit Server VM (build 11.0.9+11, mixed mode)
```

## Change local JDK Version
Now in this case your local project requires to run with JDK 15 instead of globally set JDK 11. Use jenv local setup for this
requirement as follows:


* Change into a directory, **Documents** in my case.
* Check java version, which will be 11 since we last set global one to 11.
```
    cemal.onder@C02DM1Y9MD6R Documents % java --version
    openjdk 11.0.9 2020-10-20
    OpenJDK Runtime Environment (build 11.0.9+11)
    OpenJDK 64-Bit Server VM (build 11.0.9+11, mixed mode)
```

* Set local version to 15
```
jenv local 15
```

* Check your java version again
```
    cemal.onder@C02DM1Y9MD6R Documents % java --version
    openjdk 15.0.1 2020-10-20
    OpenJDK Runtime Environment (build 15.0.1+9)
    OpenJDK 64-Bit Server VM (build 15.0.1+9, mixed mode, sharing)
```
Be aware of that a file with name **.java-version** is created in your directory. You may want to add it to .gitignore of your
project.

## Use different JDK versions with Maven
By following similar approach we can set up different JDK versions globally or per project to use it with Maven.
* Install maven
```
brew install maven
```

* Enable maven and export jenv plugins
```
jenv enable-plugin maven
```

```
jenv enable-plugin export
```

* Check your maven version
```
    cemal.onder@C02DM1Y9MD6R ~ % mvn --version
    Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
    Maven home: /usr/local/Cellar/maven/3.6.3_1/libexec
    Java version: 11.0.9
```
* Now change into a directory where you set another jdk version with jenv local. In this case I will change into my 
Documents directory which I setup before.
* Check your maven version again
```
    cemal.onder@C02DM1Y9MD6R Documents % mvn --version
    Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
    Maven home: /usr/local/Cellar/maven/3.6.3_1/libexec
    Java version: 15.0.1
```

## Resources
* https://www.jenv.be/