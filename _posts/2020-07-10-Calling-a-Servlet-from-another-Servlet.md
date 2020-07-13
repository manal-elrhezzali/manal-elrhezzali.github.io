---
title: Calling a Servlet from another Servlet
author: El-rhezzali Manal
date: 2020-07-10 7:15:00 +0800
categories: [Blogging,Servlet and JSP]
tags: [Servlet]
pin: true
---

## A- **Introduction**


Greetings!

Today we're going to talk about **Servlets** and we will mainly focus on **Calling A Servlet from another Servlet**.

Servlets are the Java programs that runs on the Java-enabled web server or application server. 
They are used to handle the request obtained from the web server, **process the request**, **produce the response**,
then **send response back to the web server**.

## B- **Calling A Servlet from another Servlet**

 
Let’s say you have an index.html page wich contains a form :

![Spring Framework ]({{ "/assets/img/sample/0.png" | relative_url }})

and a **SqServlet**  that calculates the square of a number :

![Spring Framework ]({{ "/assets/img/sample/1.png" | relative_url }})

and an **AddServlet** which performs the addition of two numbers and displays the result: 

![Spring Framework ]({{ "/assets/img/sample/2.png" | relative_url }})

and you want to call this **SqServlet** from your **AddServlet**.To do that we have two options using: **RequestDispatcher** or  **Redirect** .


#### 1. **RequestDispatcher**

  so how do we use a RequestDispatcher?
  
  First ,you need to create an instance of **RequestDispatcher** ( which is an **interface**) by doing like so: 
  
  **RequestDispatcher rd = req.getRequestDispatcher(“url”);**  // req is a request object
  
  **rd.forward(req, res);** // to send the same request and response objects  of the AddServlet to the SqServlet

  ![Spring Framework ]({{ "/assets/img/sample/3.png" | relative_url }})
 
  then you have to mention the SqServlet **mapping** in **“web.xml”** file with url-pattern being the url that we passed to **getRequestDispatcher(“url”)** which is “sq” in our case : 
  
  ![Spring Framework ]({{ "/assets/img/sample/4.png" | relative_url }})

  So now when you run your application, you get :  
  
  ![Spring Framework ]({{ "/assets/img/sample/5.png" | relative_url }})
  
  and after clicking submit :
 
  ![Spring Framework ]({{ "/assets/img/sample/6.png" | relative_url }})
  
  Now we are able to **call a Servlet from a Servlet** .But now we need the AddServlet to be able to  pass variable k to the SqServlet,normally when we want to share data between different Servlets ,we use a concept of **Session Management** but the easiest way is **put data in the request object that you are forwarding** : 
  
  req.setAttribute(“k”,k) ; // the first k is a key and second is the value so when you want to refer to this value in the other Servlet you refer it as k
  
  ![Spring Framework ]({{ "/assets/img/sample/7.png" | relative_url }})
  
  and in your SqServlet you need to fetch the data k from the request object using : 
  
  **int k = (int)req.getAttribute(“k”);** // getAttribute returns an object that is why we need to convert it to an int
  
  ![Spring Framework ]({{ "/assets/img/sample/8.png" | relative_url }})
  
  Now after running the application and submitting the two values ,you get : 
    
  ![Spring Framework ]({{ "/assets/img/sample/10.png" | relative_url }})
  
  **Note:** When you use **RequestDispatcher** ,the client(Browser) doesn’t even know who is sending the response(is it SqServlet or AddServlet? ).In fact,even though the SqServlet is the one returning the response ,in the URL the address is still for AddServlet.And keep in mind that **RequestDispatcher** works fine if your Servlets are on the same website.

#### 2. **sendRedirect**

Imagine we have a Servlet S1 that belongs “amazon” and another servlet S2 that  belongs to “paypal”.In this case,the request to S2 should be sent from the browser (the client).

So for example,when you click buy this item button on “amazon” ,S1 will inform the browser that is getting redirected to “paypal”(S1).

And here you use a method called **sendRedirect()** instead of **RequestDispatcher** because when using the **RequestDispatcher** the client doesn't know that he’s getting redirected .

![Spring Framework ]({{ "/assets/img/sample/11.png" | relative_url }})

In redirect, you basically send **two different request objects** .
So if you want to send data from S1 to S2 you have to use a concept of **Session Management**.

In our case, the AddServlet is a response to client by saying you need to go to “sq” (**res.sendRedirect(“sq”);**) and then the client sends another request to the SqServlet.

![Spring Framework ]({{ "/assets/img/sample/12.png" | relative_url }})

And since in sendRedirect we don’t forward **response** and **request** objects to the other Servlet, how do we send the value of k from AddServlet to SqServlet? 

Remember that in the SqServlet we have a **doGet()** method so the servlet fetches the data from the URL , let's use **getParameter(“k”)** method and **rewrite the URL** of the sendRedirect(“url”) method which is in the AddServlet to make it pass the value we need in the other servlet.So your servlets should look like the following:

* The AddServlet:

    ![Spring Framework ]({{ "/assets/img/sample/13.png" | relative_url }})

* The SqServlet:

    ![Spring Framework ]({{ "/assets/img/sample/14.png" | relative_url }})

then you’re application will work perfectly.

This technique of **URL rewriting** comes under the concept of **Session Management** where you can transfer data from one servlet to another with the help of : **cookies** ,**sessions** or **URL rewriting**.

######        **Sessions** :

A session is a way to store information (in variables) to be used across multiple  pages.The information is stored on the server.

So let’s say you want to use the same value in multiple servlets.In this scenario,you need to maintain the data through sessions by using the **HttpSession** interface .And this interface’s object will be provided by TomCat you just have to get the hold on it like so: 

**HttpSession session = req.getSession();**  :

![Spring Framework ]({{ "/assets/img/sample/15.png" | relative_url }})

and to make the session hold your data, use : **session.setAttribute(“k” ,k );** .

Now to  fetch the data ,in the other serlvet “SqServlet”,get a hold on the session and use **session.getAttribute(“k”);**.

![Spring Framework ]({{ "/assets/img/sample/16.png" | relative_url }})

Now after you are done with the data ,you can remove its attribute like so:

![Spring Framework ]({{ "/assets/img/sample/17.png" | relative_url }})


######        **Cookies** :

A **cookie** is a small file that is saved on the visitor's computer.
This file contains text and allows you to **remember** information about the visitor.

To create a cookie ,we use the **Cookie** class , the constructor has 2 parameters (“name”,string value) and after that you need to add the cookie you created to the response object because you are sending it to the client :**res.addCookie(cookie);**.

This means that the AddServlet will send the response and the cookie to the client and the client again will send a request  to SqServlet and he sends the cookie as well.

![Spring Framework ]({{ "/assets/img/sample/18.png" | relative_url }})

To fetch the cookie from the request object sent by the client ,use **req.getCookies()** which **returns an array of cookies**:

![Spring Framework ]({{ "/assets/img/sample/19.png" | relative_url }})

If you want to know the **differences between Cookies and Sessions** ,check **Fifi's answer** in the link below:

https://stackoverflow.com/questions/6253633/cookies-vs-sessions



##### That was all for this blog,I hope you enjoyed it and you understood all the points that we have touched on.Thank you for reading my blog! And don't forget to upvote 👍 it.
