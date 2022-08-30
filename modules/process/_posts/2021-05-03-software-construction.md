---
title: Software Construction
---

# Software Construction

__Slide Deck__   
[Software Construction: IDEs and SCM](https://docs.google.com/presentation/d/1EmPO6DpLF4FrSBxlhn7yWRsWihS7p2mmLlOBW34CxW8/edit?usp=sharing)

<iframe width="800" height="450" src="https://www.youtube.com/embed/IVBtOLiXs0A" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Engineering vs. Construction

This may seem slightly pedantic, but we need to differentiate between "software engineering" and "software construction" before we get any further.  It would be reasonable for someone to see the term "software engineering" and think that it is all about the nuts and bolts of actually putting software together - using a programming language, bringing in some libraries, maybe some build tools, etc.  And, yes, all of that is wrapped up in the grander world of "software engineering," but it's just one aspect.  We are going to use the term "software construction" to refer to all that stuff we just mentioned.  (NOTE: a lot of this material is going to be in the new CS 3140 course!)

We expect you as budding software engineers to get some exposure to the details of software construction through this course.  We also expect you to follow some of these best practices so that you start creating good habits for yourself.

# Example Best Practices of Software Construction

This is by no means an exhaustive list, but it's a good start.

## Coding Standards

Every programming language has a set of "agreed upon rules" for how you should write the code in that language.  This goes beyond the syntax of the language.  This is getting more at the style of how you write the code.

For instance, if you wrote ``coolFunctionName`` in your Python code, that would go against the coding standards of the language.  Python doesn't use camel casing, it uses underscores: ``cool_function_name``.  There's documents for every programming language that specify what you should or should not do.  Python's can be found at [https://peps.python.org/pep-0008/](https://peps.python.org/pep-0008/).

Why does this matter?  Maintainability.  Code that all follows the same standards is easier to read and easier to reference in other parts of the code.  

## Refactoring / Collective Code Ownership

When you work for a company, you don't own your code.  We mean that both literally (... you don't actually own it) and somewhat figuratively (you aren't the only person that will ever work on it).  So, when you write code, follow the coding standards so others can modify it later on if necessary, but also take the time to revisit and revise your code to improve it.  Refactoring can have benefits for the users (e.g. things might run a bit faster), but it's really for the developers, so that the knots you tied up in your code are easier to undo later on.

## Minimal Viable Product

Basically, whatever is on your ``main`` branch in GitHub should be something that actually compiles and runs.  Never commit code to the ``main`` branch if it's not tested and ready!  Make other branches to add your feature or fix a bug, then make sure it works correctly before pushing it to ``main``.  A member of your team should always be able to clone ``main`` and have "the last working major version of your system."

## Use an IDE

There is no shame in using an IDE like PyCharm or Visual Studio or anything that does things like code completion.  The whole reason we have these tools is to help _prevent_ programmers from making mistakes in the first place!  Take advantage of tools that help you build the best software.

## Use Source Control and Commit Often

Get in the habit of using git and GitHub right now.  There is absolutely no excuse for any programmer to lose their entire project due to a computer failure.  Even for your own pet projects, create a GitHub repository and be diligent with how you use it.  Not only will your project be backed up, you'll have a history where you can go back to old versions or you can add the repository to a public set of repos that can be a professional portfolio.  

## Write Tests and Actually Run Them

As much as it may pain you to "take the time to write tests," consider how much time you are saving by writing small tests as you go that you can run to verify your system at the push of a button instead of uncommenting all those ``println`` statements that you thought were such a good idea back when you were first writing the code.