---
title: Django and MVC
---

__Slide Deck__   
[Django and MVC](https://docs.google.com/presentation/d/1_gaSPHCczdsxXwmkhkYiWqZchTxHTzs-r6yyAR5Lznw/edit?usp=sharing)

# Web applications vs. Desktop Applications

Before we dive into Django and MVC, we need to first explain how web applications are fundamentally different from Desktop applications. In a desktop application, we typically run a program on one computer for one user, and when the user is done, they close the application. Data is often persisted ("saved") locally on the computer. In a very simple desktop application, there may be no user interaction at all beyond perhaps some command-line arguments. In that case, the program runs until it completes, and then terminates.

However, with web applications, we typically want a *persistent* application that is driven by asynchronous events. That is, we cannot predict precisely when and how users will interact with our webservice, and so we don't try. In modern web application development, we strive for **statelessness**.

## Statelessness

In a stateless web application, the web server doesn't store any information about a user's *state* on the server memory. Rather, as the user uses the website, each URL acts as sort of a "functional call" that modifies the websites long-term storage (database). 

As an example of this, open amazon.com and add some book to your shopping cart (might I suggest [__Clean Code__ by Robert Martin](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882). Now, close your browser, and open amazon.com on your phone or another device, log-in, and you'll see the same item in your cart.

That's because, when using Amazon before, your cart wasn't tied to any state of your web browser communicating with Amazon's servers. Rather, adding a book to your cart was a transaction. That transaction was recorded in the website's database, not stored in the server's memory.

Now compare this with older websites Collab and SIS. Both websites rely on "stateful" context connections:

![img.png](/img/arch/djano-mvc/statefulness.png)

Here, you can see when we hover over a class, we see a function. This javascript function specifies argument `CLASSROSTER$1`, but that `$1` indicates (in the above example) the class at index 1 in the courses table. That means this function *only* works because of the context. So, if we were to open that roster, copy the web-url, closer our browser, and then re-open and paste, **it wouldn't take us to the same place**. That's because this website is relying on the *context* (or "state") the user is in. This contributes to several issues with Collab and SIS. Namely:

* The maximum user capacity of both websites can handle is comparatively lower than it could be, as significant memory is required to manage each user-connection
* This is why the back button doesn't work, or why you can't copy and paste URLs to classes on SIS like you can with books on Amazon

## MVC

Now we're ready to talk about MVC. MVC (Model-view-controller) has become extremely widely adopted in application development (both for web applications and GUI applications). MVC has three components:

* Model - the portion of the system that handles data. Typically, the model will interact with a database to store and retrieve system data. All "state" information should be stored in the database, and never on the server itself.
  * Be aware, the model **is not the database**. The model handles the *interactions* with the database.

* View - the portion of the system that handles creating and rendering the user interface. Whether this is generating HTML pages, creating dynamic user interfaces with buttons, fields, etc., or simply returning raw data using something like JSON, any "output" of the application is rendered by the view.

* Controller - Responds to user input. Based upon user input, it may:
  * Interact with the model to store or retrieve information from the data model objects
  * Handle any business logic
  * Send information to the view to be rendered

![img.png](/img/arch/djano-mvc/mvc-diagram.png)

This gives us the benefit of **separation of concerns**, and helps us to write reusable code.

## Django

In this section, we will give a very brief overview of Django structure. A full tutorial [can be found here](https://docs.djangoproject.com/en/4.1/intro/tutorial01/).

Django is an MVC framework, although they use the nomenclature model/view/template. As such, `views.py` ends up being what we would think of as the **Controller**, and not the View.

### App file structure:

Within a given app, we have the following files and folders:

* `models.py` - The **model** lists our ORM (Object relational model classes) - One advantage of Django is that Django will handle all the database interactions (SQL queries, for example) for you. You only have to define your data classes in `models.py`.

* `views.py` - The **controller** (not the view) - lists a menu of functionalities of the website. This could include things like "display a web page with all of the survey questions" or "display the results for *this particular* survey question". Some of the options may perform invisible interactions without displaying their own webpage (such as the function `vote` from the Django tutorial)

* `urls.py` - Connects the urls the user interacts with the the functions and classes in `views.py`. You can think of `urls.py` as a traffic cop, that directs requests from users (which come in via urls) to the correct `views.py` function or class.

* `templates/[appname]` - The **view** - this folder contains the .html template files that are used to generate the web pages users receive back from the server. The actual code that *builds* these web pages from the templates and data provided by the *controller* is handled by the Django framework itself. As such, you only need to define a **template** for the .html page.