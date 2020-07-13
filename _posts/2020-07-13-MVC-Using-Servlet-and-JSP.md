---
title: MVC Using Servlet and JSP
author: El-rhezzali Manal
date: 2020-07-13 6:20:00 +0800
categories: [Blogging,Servlet and JSP]
tags: [Servlet]
pin: true
---

Greetings!

In this blog, we'll create a small web application that implements the Model View Controller (MVC) design pattern, using basic Servlets and JSPs.
We'll explore a little bit about how MVC works, and its key features before we move on to the implementation.

## **Introduction to MVC**

**MVC** stands for Model View and Controller. It is a **design pattern** that separates the business logic, presentation logic and data.

#### 1. **Model Layer**

* This is the data layer which consists of the business logic of the system.
* It consists of all the data of the application
* It also represents the state of the application.
* It consists of POJOs (classes) which have the connection to the database.
* The controller connects with model and fetches the data and sends to the view layer.
* The model connects with the database as well and stores the data into a database which is connected to it.

#### 2. **View Layer**

* This is a presentation layer.
* It consists of HTML, JSP, etc. into it.
* It normally presents the UI of the application.
* It is used to display the data which is fetched from the controller which in turn fetching data from model layer classes.
* This view layer shows the data on UI of the application.

#### 3. **Control Layer**

* It acts as an interface between View and Model.
* It is a Servlet (a class that extends HttpServlet).
* It intercepts all the requests which are coming from the view layer.
* It receives the requests from the view layer and processes the requests and does the necessary validation for the request.
* This requests is further sent to model layer for data processing, and once the request is processed, it sends back to the controller with required information and displayed accordingly by the view.

#### 4. **Service Layer**

Between the controller and the model sometimes goes a layer which is called a service. It fetches data from the model and lets the controller use the fetched data. This layer allows to separate data storage (model), data fetching (service) and data manipulation (controller). Since this layer is not part of the original MVC concept, it is optional in most cases but can be useful for code management and reusability purposes in some cases.

#### The advantages of MVC are:

* Easy to maintain
* Easy to extend
* Easy to test
* Navigation control is centralized

## **Example of MVC With Servlets and JSP**

To implement a web application based on MVC design pattern, we'll create a **Student** class which will act as our Model layer and a **StudentService** class which will act as our Service layer.
**StudentServlet** class will act as a Controller, and for the presentation layer, we'll create **student-record.jsp** page.
Now, let's write these layers one by one and start with **Student** class:

![Spring Framework ]({{ "/assets/img/sample/Blog4-0.png" | relative_url }})

Let's now write our **StudentService** which will process our business logic:

![Spring Framework ]({{ "/assets/img/sample/Blog4-1.png" | relative_url }})

Now let's create our Controller class **StudentServlet**:

![Spring Framework ]({{ "/assets/img/sample/Blog4-2.png" | relative_url }})

This servlet is configured by annotations and it is the controller of our web application.

First, it reads a parameter id from the request. If the **id** is submitted, a **Student object** is fetched from the business layer.

Once it retrieves the necessary data from the Model, it puts this data in the request using the **setAttribute()** method.

Finally, the Controller **forwards** the request and response objects to a JSP, the view of the application.

Next, let's write our presentation layer **student-record.jsp**:

![Spring Framework ]({{ "/assets/img/sample/Blog4-3.png" | relative_url }})

And of course, the JSP is the view of the application; it receives all the information it needs from the Controller, it doesn’t need to interact with the business layer directly.

##### In this blog , we've learned about the MVC i.e. Model View Controller architecture, and we focused on how to implement a simple example.I hope you enjoyed it and you understood all the points that we have touched on.Thank you for reading my blog! And don't forget to upvote 👍 it.
