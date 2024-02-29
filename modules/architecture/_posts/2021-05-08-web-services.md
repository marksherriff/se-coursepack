---
title: Web Services
---

# Web Services

__Slide Deck__   
[MVC and REST](https://docs.google.com/presentation/d/1OqDykKXiGcjPC-HCtXzUIv3EvY7eFml0qrE07nPueSM/edit?usp=sharing)

[MVC and REST - Spring 2024 Update](https://docs.google.com/presentation/d/1UATEbAs1E98E6U8f6RayEftA8DU2VA7V747yl5nmOt0/edit?usp=sharing)


<iframe width="800" height="450" src="https://www.youtube.com/embed/hgVHwkLVCLI" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


Now that we know how individual web applications are built and we know the architectural design patterns used to build those apps… what can we do with them?

Part of the power of MVC is that you can swap out parts of the M, the V, and the C without affecting the rest of the application too much (of course this depends on some things, but go with me here…). Right now, you can go to your project’s website and access it with a web browser. Which is good. But what if, for instance, you wanted to make your data accessible by other apps? What if you wanted to combine the meet-up app with the civic connect app in some way? Perhaps if you have an account on one, it will log you in to the other? Or maybe the preferences you store in the civic connect app helps you refine your searches on the meet-up app?

We accomplish this by creating web services (what you probably have heard of as REST APIs). Basically, we want to start focusing on building out the best part of our app as our “core functionality” - something that we are doing to add value to the world. But we utilize the services of other apps for things we don’t necessarily want to program again. Like login - and what you are doing with Google. That’s a web service. Payment is another good option. You don’t want to have to write code to handle financial transactions. So, it’s probably worth it to your bottom line to pay just a bit per transaction to use Square or PayPal or something like that.

That’s the power of modern web applications! We are now building with pre-existing “functionality Legos” to make bigger and better applications faster and more reliably!