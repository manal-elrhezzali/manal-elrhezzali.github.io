---
title: Understanding spring’s foundations (The spring Framework)
author: El-rhezzali Manal
date: 2020-07-04 15:04:00 +0800
categories: [Blogging, Tutorial]
tags: [spring]
pin: true
---

![Spring Framework ]({{ "/assets/img/sample/firstBlog/springframework.png" | relative_url }})



## **Introduction**

Greetings!

The spring Framework is a universal,
reusable software environment that provides particular functionality(like web development and data access)
 as a part of a larger software platform to facilitate development of software applications,solutions and products.
 The spring framework was the beginning of Spring .
 It was created to simply the development process and it became the foundation for which all spring projects were built upon.
 Applications could then in turn utilize these projects along with the spring framework,
 to even further simplify their development.
 
## **The six key areas of the spring framework**

The spring framework utilizes a modular architecture meaning that it’s broken up into separate individual 
components that can be connected together and each of those components is then responsible 
for providing a set of functionality and together as a whole they make up the spring framework .

![Spring's six keys ]({{ "/assets/img/sample/firstBlog/sixKeys.png" | relative_url }})

#### **Spring core**

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

#### **Spring Web**

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

#### **Spring AOP**

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

#### **Spring Data Access**

* The Spring Framework’s Data Access module makes it easier to develop 
applications that interact with data and it removes a ton of **boilerplate 
code** ( refers to sections of code that have to be included in many places 
with little or no alteration.)

 ![dataAccess example ]({{ "/assets/img/sample/firstBlog/dataAccessExample.png" | relative_url }})
 ![dataAccess example ]({{ "/assets/img/sample/firstBlog/dataAccessExample.png" | relative_url }})

* **Database transactions** with the spring framework’s Data Access module are really easy.
**A database transaction** is a series of database operations that must happen together (that doesn’t necessarily mean that they all happen at once ) or not at all.

  For example: 

  ![dataTransaction example 1]({{ "/assets/img/sample/firstBlog/exapleTransaction.png" | relative_url }})
  Transferring money between two bank accounts ,
  you first have to subtract the  amount  from the first 
  account and then you add that amount to the second account.
  And if the subtraction of the money succeeds, but the addition fails,
  then the money’s lost. And likewise,if the subtraction fails ,
  but the addition succeeds,then somebody just got that amount for free.
  So as you can see transferring money between two bank account must be 
  transactional. It must happen all together or not at all.
 
  ![dataTransaction example 2]({{ "/assets/img/sample/firstBlog/example2Transaction.png" | relative_url }})

* Another small ,but useful feature provided by the Data Access module is **Exception Translation**( Exceptions are an event within a program that disrupt execution).
  The problem this feature solves is that different database vendors use different errors and exceptions for the same class of errors.

  For example:
   
   ![Exception translation]({{ "/assets/img/sample/firstBlog/exceptionTranslation.png" | relative_url }})
  The Data Access module of the Spring Framework helps by taking these database-specific error codes and translating them into a well-known set of exceptions.
   
   ![Exception translation]({{ "/assets/img/sample/firstBlog/exceptionTrans2.png" | relative_url }})
  
* **Testing data** is easier with the spring framework’s Data Access Module.Since Spring framework is managing the configuration and the set up of how an application accesses its
  data, it’s easy to switch out that configuration for testing.During testing it’s common to utilize an **embedded test database**.You certainly wouldn’t want to be running your tests with important production data, and Spring’s Data Access support helps to set up that embedded test database and ensure that your code points to that during tests.

   ![EmbeddedDB]({{ "/assets/img/sample/firstBlog/EmbeddedDB.png" | relative_url }})
  
#### **Spring Integration**

In this section ,we will briefly take a look at the features that the Spring Framework provides for integration.

* Applications don’t live in isolation that needs to share data and work with other apps.
* **Integration** is all about making different systems and applications work together.
* So how does one application “talk” to another?This is a multi-sided problem:
     - How do you expose operations to other systems?
     - How do you invoke or run operations on other systems?
* There are many Different Ways to expose operations to other systems:
     - RMI (Remote Method Invocation)
     - Messaging Systems
     - Web Services (which is the most popular): are simply operations that are exposed and accessible via the web.
     And the spring framework makes it easy to both expose and invoke web services.
  **Example of web services**: expose an operation: looking up an account by its id
  ![webServices]({{ "/assets/img/sample/firstBlog/webServices.png" | relative_url }})
 
  **Example of web services**: invoke our service within another application
  Spring Framework provides support for invoking our REST service,and you utilize something called a RestTemplate which abstracts away tedious(boring) details like : 
     - Connecting to the web service
     - Sending the command
     - Handling the response from the web service
   
   ```java
   restTemplate.getForObject("http://foo.com/account/123",Account.class);
   ```
* **RestTemplate** makes calling web services as easy as one line.
* **Just call the service** and RestTemplate **takes care of the “rest”**.

#### **Spring Integration**

* Testing is an important part of developing software , 
so it’s no surprise that the Spring Framework strives to 
help in this area as well.And there’s many different levels at which software is tested, 
and the spring framework focuses on two different areas, on Unit testing and Integration 
testing .

1. **Unit testing**: 
   - Let’s start by talking about Unit testing : is 
   a software development process in which the smallest testable 
   parts of an application,called units,are individually and independently scrutinized 
   for proper operation.
   - The Spring Framework support for testing largely comes as a side effect of using 
   Dependency Injection.
   - How does **DI(Dependency Injection)** help make testing easier?
         
       * with unit testing, the idea is to test 
           the smallest unit of code possible,and when 
           the code that’s being tested has no dependencies ,
           the unit testing becomes a fairly easy process.
           In this case the developer is forced to declare what the code depends on.
           **So during testing dependent code can be replaced with code that 
           behaves certain way** and this action of replacing pieces of 
           code with controlled code is called **Mocking**.
           
       * however ,when the code under test has dependencies ,it’s important 
           to be able to control how those  dependencies behave in order to 
           restrict the testing to just the code and not the dependencies.
           For example:
           
           ![UnitTesting]({{ "/assets/img/sample/firstBlog/unitTesting.png" | relative_url }})
           
           This code has been written with DI in mind and declares that it depends on the 
           SecurityManager.During testing ,we can mock this dependency and control what 
           security clearance level is returned.
           
       * Spring Framework comes with several built-in mocks to make testing easier and faster.

2. **Integration Testing**:
   is the phase in software testing in which individual software modules are combined and tested as a group.
   It occurs after unit testing.Integration Testing is focused on how various parts of a an application integrate together.
        
      * Spring Framework provides support for **piecing together parts of an application** for testing.
      * Spring Framework provides support for **common integration testing scenarios**: testing data access ,whole parts of a web application.
      * Spring Framework provides support for **cleaning up after tests**: test modify things,need to reverse modifications after test so as to not
        affect the next tests.


##### Thank you for reading! If you enjoyed it, please clap upvote 👍 it.
















