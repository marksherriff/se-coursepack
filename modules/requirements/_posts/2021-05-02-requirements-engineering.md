---
title: Requirements Engineering
---

# Requirements Engineering

__Slide Deck__   
[Requirements Engineering](https://docs.google.com/presentation/d/1lHlHBVp0VXUlOp3s9hLqi5Qc45CaguopoqGNud8i1j4/edit?usp=sharing)

<iframe width="800" height="450" src="https://www.youtube.com/embed/nTkgjl5AR-Y" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Solving the Right Problem

First, a brief example:

> Imagine that you have been hired to build a digital version of a classic board game.  You spend days finding the right graphical assets.  You spend even longer researching different AI methods for the CPU opponent.  You read rule book after rule book, making sure that even the most random corner case of your gameplay is covered.
> 
> After months of hard work, you finally show your finished game to the client: Chess Master 3000.  You beam with pride as the boot it up for the first time.
> 
> The client... looks less than enthusiastic.  "Where is the game you built for me?" they ask.  
> 
> You blink at them, confused.  "It's... right there?  Don't you like it?"
> 
> The client sits back and takes a deep breath.  "Well... it's a very nice chess game.  But I asked for checkers."

Okay, I realize that this is a bit overdramatic.  But still, while you might not build _a completely different program_ than what the client wants, it is entirely possible to get some aspects wrong.  Perhaps you aren't familiar with their domain knowledge and you implemented something incorrectly because you simply didn't know that something wasn't allowed, like programming SIS to allow a student to take two classes at the same time.

__Requirements engineering__ is the subfield of software engineering completely focused on making sure that we can turn the plain-language explanation of what a software need is into something that is actionable by a development team.  The process is typically broken into two broad categories:

* _Requirements analysis or elicitation_ is the process of actually gathering the requirements from stakeholders
* _Requirements modeling or specification_ is the process of turning those needs/statements/conversations into something that can be turned into code

# Types of Requirements

Before we get into elicitation vs. specification, let's define some different types of requirements.

## Functional Requirements

A __functional requirement__ is a statement of what the system should specifically "do."  It represents a feature of the system that is:

* specific and unambiguous
* measurable and observable
* testable in some way to determine if the requirement has been met

These are often expressed in a form kind of like this:

> The system shall _//do something//_ because _//important reasons//_ for _//these types of users//_

So anything like the following for a to-do list app:

> The system shall allow a user to add a new to-do list item by tapping the plus icon on the home screen.    
> The system shall mark an item as "Completed" if the user taps on the checkbox beside the item.    
> The system shall allow the user to sort to-do items by their due date, with the earliest date first.   

## Non-Functional Requirements

A __non-fuctional requirement__ (or NFR for short) is a statement regarding an overall condition of the system and _is not_ directly tied to a single function or feature.  NFRs often fall under one of these categories:

* security
* privacy 
* usability 
* accessibility
* reliability 
* availability 
* performance

No one feature in a system is responsible for it's security, for example.  It is an aspect of the system that has to be taken into consideration with every feature.  Thus there has to be some sort of centralized, concerted effort among all developers to ensure that NFRs are completed

## Contraints

A __constraint__ is a limitation put on the "solution set" of possible systems that could be developed.  For example, a client may say that the software you build for them must run on iOS.  If this is the case, they have created an implementation limitation on all the possible ways that you could build something.  Another example could be that you have to utilize some particular API or third-party service due to contractual obligations.  These are all constraints and not functional or non-functional requirements.
