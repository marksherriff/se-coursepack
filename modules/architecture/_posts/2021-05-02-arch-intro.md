---
title: Architecture Introduction
---

# Architecture Introduction

<iframe width="800" height="450" src="https://www.youtube.com/embed/2cXgwQA4wVQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> __Slide Deck:__ [Architecture Introduction](https://docs.google.com/presentation/d/1lIlIkh2t8wNotMOT0m863CKaY1omdGbz8mn0k_9Zqe8/edit?usp=sharing)

How should you broadly design your system so that you can add to your software overtime easily?

As we build our software systems, we must be aware of software entropy. Software entropy refers to the fact that as a software system ages (not in time, but in number of changes), each change is more likely to cause unexpected problems or failures, or necessitate significant changes to large portions of the software’s implementation. Selecting the right architecture can help us avoid these pit falls. In this lecture, we will specifically discuss peer-to-peer architecture, layered architecture, and three-tiered (user interface, business logic, and data) architecture. In the next two weeks, we will also discuss in great detail MVC (Model-View-Controller), which is the core architecture for django.