---
title: Software Process
---

# Software Process

__Slide Deck__   
[Software Process and Methodologies](https://docs.google.com/presentation/d/1JW2Ci1oqMJyYIirwo-VaKeC_4BujxM0eKQoNGlQuMs8/edit?usp=sharing)

<iframe width="800" height="450" src="https://www.youtube.com/embed/DybqiqW27h0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Why do we need a process?

Think back on when you first learned to code.  Maybe it was an assignment in an introductory course.  How did you go about starting a program you wanted to write?  

My guess is that there were a few potential starting places:

1. You read the instructions, hopefully more than once.
2. You took out a piece of paper or maybe a blank text document and wrote out some notes.
3. Maybe you drew a picture of what the program would do.
4. Or... you just started coding and hoped you'd arrive at a solution eventually.

These aren't necessarily bad ways to start a program, but they only really work (to varying degrees, mind you) if you are working alone or with a very small team.  With more people, you need a bit more planning to make sure everyone is working together toward the same solution.

When we consider any other form of engineering, there are a number of concrete, specific steps that engineers take in order to complete a job on time, on budget, safely, and meeting the specifications of the customer.  This is no different for software!  The problem (and advantage!) is that software can be more easily changed during and after construction than, say, a five-story office building or an airplane.

So, we need a repeatable process to follow when we build software.

# The Phases of Development

Broadly speaking, the five phases of software development are:

1. Requirements: determine what the stakeholders need and then communicate those needs to the development team
2. Design: determine what the best way is to construct the solution
3. Implementation: build the software
4. Testing: ensure the software that was built was the correct solution and operates within tolerance levels
5. Maintenance: continue to support the software into the future

This is an oversimplification, as each of these phases has more going on than just the title indicates, but it's good enough as a reference.  

A software development process (or methodology if we are talking about a specific instance of a process) takes these phases and stipulates how each phase will be implemented, to what degree, and how iteration will be taken into account.

A number of factors can have an impact on what type of software methodology you choose.  For example:

* Is the team co-located or is it global?  If it's global, you will probably need to have more documentation of the requirements and design that everyone can reference.  If it's co-located, then there can be more informal discussions.
* Is the primary client "available" to the devleopers?  If they are, then the developers can just ask the client for clarification on a requirement whenever it is needed.  But if the client is a very large group of users (e.g. users of Microsoft Windows), then there needs to be some proxy for what the users might want.
* What is the culture of the office like?  A more laid back environment tends to lend itself more toward informal conversations, designs on whiteboards, etc.  A more formal environment typically means more documentation and rigid steps to approve software changes.
* Are there any regulatory issues?  If you are building software for an airliner, then you will need FAA approval, and that _always_ means more detailed documentation, designs, and testing specifications.  If you are building "Grandma Rachel's Recipe Keeper"... well, let's hope Grandma Rachel is a bit more understanding about documentation needs.

# Types of Software Processes

In general:

* A _plan-driven methodology_ is one that is heavier on documentation and specification, relying more on design documents than customer interaction, and tends to address risks up front.  It is more often used in larger software teams, teams that are widely distributed, and for software that is highly safety critical.
* An _agile methodology_ is one that focuses much more on immediate value for the customer, rather than spending time and resources on extensive documentation.  It is more often used with smaller teams, for projects that require a quicker turnaround, and for software that does not require any regulatory oversight.

Both of these types of processes allow for various forms of iteration over each of the phases, just implemented in different ways.  This is different from the "proto-process" - the Waterfall Model, which does each of the five phases, in order, without the ability to "go back" to a previous phase.