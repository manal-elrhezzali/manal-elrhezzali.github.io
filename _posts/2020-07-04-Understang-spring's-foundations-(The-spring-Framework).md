---
title: Understanding spring’s foundations (The spring Framework)
author: El-rhezzali Manal
date: 2020-07-04 18:30:00 +0800
categories: [Blogging]
tags: [spring]
pin: true
---

![Spring Framework ]({{ "/assets/img/sample/firstBlog/springframework.png" | relative_url }})



## **Introduction**

Greetings!
 Today we're going to talk about **three out of six** key areas of the spring framework.
 The spring Framework is a universal,
 reusable software environment that provides particular functionality(like web development and data access)
 as a part of a larger software platform to facilitate development of software applications,solutions and products.
 The spring framework was the beginning of Spring .
 It was created to simply the development process and it became the foundation for which all spring projects were built upon.
 Applications could then in turn utilize these projects along with the spring framework,
 to even further simplify their development. 
 
 
## **Three out of six key areas of the spring framework**

The spring framework utilizes a modular architecture meaning that it’s broken up into separate individual 
components that can be connected together and each of those components is then responsible 
for providing a set of functionality and together as a whole they make up the spring framework .

![Spring's six keys ]({{ "/assets/img/sample/firstBlog/sixKeys.png" | relative_url }})

#### 1. **Spring core**

Spring core is one of the most important ,
if not the most important pieces of the spring framework.
It serves as the foundational module upon which every other module is built.

![Spring Core ]({{ "/assets/img/sample/firstBlog/springCore.png" | relative_url }})

Dependency injection is about dealing with the way objects fulfill their dependent objects and it comes at the center of Spring Core.

There is mainly two different choice for fulfilling object dependencies:

1. The object fulfills its own dependencies.(**tightly coupled objects**)
2. The object declares what it depends on and something else fulfills the dependency.(**more flexible and loosely coupled objects**)

The best choice is number 2 because 
the first option creates tightly coupled 
objects and  for example if someone wants to buy a 
computer they can’t change or upgrade the memory 
because when the computer was created , 
the memory was created as part of it then if you want 
to change or upgrade the memory,you’d have to buy a whole 
new computer.Unlike choice number two of declaring our 
dependencies is much more flexible.the object and its 
dependencies are loosely coupled because you can change 
one without having to change the other.  

Spring core is a Dependency injection container.
You can utilize it to declare objects and their dependencies 
and spring core will create , 
manage and connect them all together.Hence this results 
in less things for a developer to manage and that is why 
it’s not uncommon to hear spring core referred to as the 
glue of the application,as it’s the thing that pieces 
together and manages many individual parts that form the 
application.

#### 2. **Spring Web**

Spring Web is a framework for handling web requests.
Web requests can be handled in one of the two different ways either via:
**Spring Web MVC** or **Spring Web Webflux**

1. **Spring Web MVC** :
   * Java language introduced very basic support for interacting with the web via a built-in framework called the **Servlet API**
     (**Servlet component**)

   * **A servlet**: is an object that receives a request and generates a response based on that request.

   * This is what a standard web request using **servlet API** looks like:

     ![Spring web  ]({{ "/assets/img/sample/firstBlog/springMvc.png" | relative_url }})

   * **Challenges with Servlet API**: low-level API 
    (it’s more detailed and offers less way of abstracting 
    complexity => less productive) and easy to mix-up 
    concerns(easy to develop application logic that lacks proper design principles.
    Code can quickly become unorganized and hard to maintain).

   * This is what a standard web request using Spring Web MVC looks like:

     ![Spring Web MVC ]({{ "/assets/img/sample/firstBlog/springWebMVC.png" | relative_url }})

     the request starts off the same entering the webserver and 
     passing through the servlet API ,however,instead of going 
     directly to the business logic ,it’s sent through to the Spring 
     web Mvc Framework.The business logic can then make use of Spring 
     Web MVC,generate a result, and pass control back to Spring Web MVC ,
     which in turn can pass control back to the Servlet API ,and ultimately 
     generate a response.

   * **Advantage of Spring MVC**: it provides a higher-level API for the developer to interact with,
     and this results in easier usage and more productivity and easier 
     to develop code that follows proper design principles. 

2. **Spring Webflux** :

In order to understand Spring Webflux purpose we first need to 
understand something called reactive programming.

   * **Reactive Programming**: is a way of  programming that 
     focuses on the streams  of data and how they change .
     And the key idea behind Reactive Programming is that react 
     to change rather than wait for change.

   * Spring reactive programming framework is called Spring  Webflux ,
     it’s primary purpose is still to handle web requests but the way in 
     which it handles them is different.Specifically,
     web requests are executed **asynchronously**,and they don’t 
     block or wait (**how that is it work?** -->the code asks to be notified when 
     the operation is complete and continues executing other operations when 
     it’s observed that the operation is complete, the code can continue executing 
     subsequent steps) and this results in better resource utilization.

#### 3. **Spring AOP**

In order to understand what Spring AOP is ,we first have to understand what AOP is.
**AOP** stands for Aspect-Oriented Programming .

* A programming paradigm that aims to increase **modularity** (organization)
 by allowing the separation of cross-cutting concerns(concerns that affect 
 many parts of an application because they span multiple layers,
 or tiers of an application).
 
* **Without AOP** ,solving concerns that are cross-cutting results in **scattered and duplicated code** across many parts of an application.

* **Benefits of AOP**: The Spring AOP has mainly two uses :

    * Used to implement features in spring.
    * A valuable tool for developers to handle cross-cutting concerns.
     
     Example: Application Security without Spring AOP
      
     ![Spring Example1 ]({{ "/assets/img/sample/firstBlog/example1.png" | relative_url }})
     
     Example: Application Security with Spring AOP
      
     ![Spring Example2 ]({{ "/assets/img/sample/firstBlog/example2.png" | relative_url }})

##### That was all for this blog,I hope you enjoy it and you understood all the points that we have touched on.In the next blog,we will talk about the remaining three key areas of the spring framework.Thank you for reading! If you enjoyed it, please  upvote 👍 it.












