---
title: "Programming Paradigms - Introduction"
date: 2019-09-17T09:16:14+03:00
lastmod: 2019-09-17T09:16:14+03:00
draft: true
keywords: []
description: ""
tags: []
categories: []
author: "cemal"
toc: true
---

# Programming Paradigms - Introduction

In these series I would like to discuss about programming paradigms shortly. First of all; What is Programming Paradigms?
It is the style or approach to writing code. We are already using one of them if we are programming. It is being used
to categorize programming languages with their features. Let me start those category distinctions and the series
by comparing most popular ones first: 

## Versus 1: Unstructured Programming vs Structured Programming***

Actually this versus is really historical. It is discussed in the middle of 19ths and it is decided by the most of the
programming languages today to use Structured Programming and avoid developers deal with Unstructured Programming which
aims for easy to understand, maintainable, bug free, extensible code.

### Unstructured Programming
This one is used very rare nowadays. Think about assembly languages, how they use ***goto*** statements to jump
around the programming flow. Using goto statements started to being considered harmful especially after 
Edsger Dijkstra's letter "Go To Statement Considered Harmful". In my own opinion, goto statements itself is not bad in
itself but it is easy to abuse by programmers and this leads to Spaghetti code. Because goto is used to simulate behaviour
of while, if statements etc so it is also hard to understand if the code is getting huge and you as a developer
must remember what is the purpose of using goto. It is used for while statement or for if statement? Let me show an
example:

#### Show Me The Code

Structured Version:
```
while( i < 10) {
   ...
}
```

Unstructured Version:
```
goto CHECK;
START:
{

}
TEST: if ( i >= 10 ) goto START;
```

### Structured Programming
We talked about goto problems and Edsger Dijkstra's letter above who is father of **structured programming** term.
It may be also called Modular Programming. Code should be maintainable, easy to understand for the current and further
developers. For these reasons new programming languages often abstracts usage of **goto** statements directly from the
developers. Instead those structured programming statements are involved; if, do, while... Briefly we can say that
most of us are using those structured programming languages currently. Keep in mind that those programming paradigms
categorizing can be nested, as we will talk in the future; there will be categories like Functional Programming vs
Object Oriented Programming, they are both inherits from Structured Programming but they have now more sub-categories
because of their different characteristics: function evaluations vs objects (or how to deal with mutability), 
will discuss in detail.

#### Show Me The Code

Structured Version:
```
if ( i < 10) {
   ...
}
```

Unstructured Version:
```
if ( i >= 10) goto NEXT;
{

}
NEXT:
```

Before going further; those paradigms are overlap each other. So for this reason there is no concrete separation on
categories, instead if you can understand those concepts you can understand which paradigms/features have your programming
language and beyond which characteristic ***you*** have as a programmer. Because most of the programming languages
doesn't force you to code in those paradigms, instead you determine which characteristic your code has. For this reason
you can hear the conversations in your team that people are coding procedural (we will discuss it) while they supposed
to code object oriented.

## Versus 2: Imperative Programming vs Declarative Programming

You can find lots of definitions like "Imperative Programming is interested in HOW the job is being done while
Declarative Programming is interested in WHAT is being done". So this may be too abstract. But while talking about
abstractions, if you are coming from OOP concepts or if you are familiar with Clean Coding or Separation of Concerns,
this Imperative and Declarative comparision will be more clean for you. Because it is about abstracting the logic
from the users and encapsulate each behaviour on its own. But if you are not familiar with those concepts, let me
try to simplify it by using some examples;

### Imperative Programming
#### Show Me The Code


### Declarative Programming
#### Show Me The Code

We talk about how we should avoid to say some languages strictly belongs some categories. This means;
you can't say Java is declarative or imperative. It depends on how you are using the language. Yes it could be forced
by the language to be declarative but it doesn't have to; think about an example:


### Functional Programming
#### Show Me The Code

### Procedural Programming
#### Show Me The Code


# References
- Goto and Branch Instructions, Dr. Orion Lawlor, https://www.cs.uaf.edu/courses/cs301/2014-fall/notes/goto/
- Notes On Structured Programming, Edsger W. Dijsktra, https://pdfs.semanticscholar.org/013b/f90f472e49c05263b90d9e36f8d2705e7fc7.pdf