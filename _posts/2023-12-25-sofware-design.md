---
layout: post
title: software design with swift method and XP/TDD
categories: software design
tags: swiftMethod XP TDD
---

Swift, not the language, is the methodology that can help development team to quickly get started the journey of modernizing their legacy system into a contemporary microservices architecture. the approach works smoothly with the extreme programming and test driven design that's getting popular recently.

## introduction

> we are doing DDD without mention it to our customer
>
> <p style="text-align: center;">--Shaun Anderson</p>

regarding software design, there were heated discussions about what is and is not design in software development process. I would recommend you to read what Jack W. Reeves his famous [essays](https://www.developerdotstar.com/mag/articles/reeves_design_main.html) on this topic.

While conventional thinking often associates design solely with architects or senior developers, various team meq   mbers contribute to the design process in distinct ways. For example, when a product manager prioritizes which features to develop first, envisioning the initial business value for end-users, it's a form of software design. Similarly, when a designer crafts intricate interaction blueprint for the system or a developer meticulously writes unit tests while envisioning system behavior in different scenarios, they are all actively participating in software design, albeit focusing on only a small part of it.

I'm going to call the notional architecture design process (swift method) as high level design, whereas choosing thin slices and backlog maintenance as mid-level design. The coding part, executed in Red-Green-Refactor cycle manner are the detailed design. 

the processes that follows, like setting up CI/CD pipeline etc. are part of the building process but not part of design.

Swift method was invented by Shaun Anderson, former pivots. you can find the [introduction](https://www.swiftbird.us/the-swift-method) from his own site. also a [talk](https://youtu.be/7-fRtd8LUwA?si=06U1JYT-34fYJKOC) at Explore DDD conference is available.

for XP and TDD, there are more resources like [its own site](http://www.extremeprogramming.org/) and the [book](https://a.co/d/6RMzF9I) by the inventor Kent Beck.

## swift method

the swift method, depends on the flavor, might take from half a week to 3 weeks.

the process I'm going to describe here took longer to complete however in a sense, might also be more practical for the beginners to follow.

### goals and anti gaols

although it seems obvious, however, setting a set of good goals and be clear what would be those not the high priority at least for now is actually quite important for the project team. 

especially if it's an enablement engagement which only last for 6 to 12 weeks. usually we'll emphasis that implement the system in full is not our goal (an anti goal). on the other hand, if we need to focus on the enablement part of the engagement, then we'll further define which aspect is more important for the team. usually the project core members might come up quite divergent objectives, it's necessary to group them into several themes and better prioritize them too.

### event storming

event storming is the activity to gather the business events that happens in and (some) around the target system. the activity itself is a much simplified form of Alberto Brandolini's [event storming workshop](https://www.eventstorming.com/).

there are several important points that should be kept in mind:
- events are those happens in and around the system that having some business value
- events should be written in past tense, one sticky for one event
- events should be arranged one after another in time elapse order from left to right. the events follows could be triggered by previous one, or just should happens next in logical order.


below is one of the example that shows how user register itself and optionally add payment method to their account.
![event storming - birds eye view of the system](/assets/images/event-storming.png)

### service identification

after events has been identified, usually we aim for 60 to 80 percent of the business events inside the system are collected on the board. it's important that we don't looking to collect all events, especially some of the trivial ones, unless you know that there are some pains or performance issue around this part of the system.

to identify the potential service candidates, we'll go through the internal events one by one and consider what business capability should be assigned to make this event possible. 

below are the guidelines while identifying the candidates:
- business capabilities
- data ownership
- loosely coupled
- testability

when you are in doubt, there are some criteria that can help you think about [whether it should be a microservice](https://tanzu.vmware.com/content/blog/should-that-be-a-microservice-keep-these-six-factors-in-mind). here is excerpts:
- rate of change
- scalability(independent)
- lifecycle management
- isolated failure
- simplifying external dependencies
- freedom of choosing other technology

here is the example of result of the process for above events collected earlier.
![service identification](/assets/images/service-identification.png)

### boris

the boris process is the key part of the whole swift method. here we follow the events flows and service candidates we identified in previous steps, try to diagram the relationships between these service candidates utilizing abstracted communication methods (only the property of synchronous or asynchronous is important here). whenever we encounter those communication protocols that out of our control, we usually marked it in different color (black) to put it aside.

here is how you transform from the events to first draft of boris diagram:
![the beginning of boris](/assets/images/boris-start.png)

when the whole flow finished, the boris looks like this:
![whole boris - spider web of the service system](/assets/images/boris-full.png)

### snapE

the snapE step has an odd name, which supposed to stand for "snap not analysis paralysis extended".

during this process, the job is to capture the internal of each important services candidates that we used in our boris diagram. by now, you should've found out that why we keep calling them potential service candidates, as they are changed, combined or split multiples already. 

when most of the diagram is complete, again 60 to 80 percent of the flows we captured during event storming phase, we should be pretty confident that the system (notional) architecture has already took shape and not changing too often even if we kept going further.

then it's time to document the internals of services, you can also do this as you working on boris though, what we want to capture are the APIs, data, high level stories and risks etc. here is are two examples:
![snapE - profile of the service](/assets/images/snape.png)

the process so far is the first iteration of you swift process. 
event though it's a demanding process (usually we'll ask the team to join full time for the whole 4 weeks.), but compare to how long the traditional process lasts. the swift method is actually match its name.

## backlog maintenance

after we've got the first version of our notional architecture, it's time to bring out our developer's gears to starting coding? no, not yet. 

### thin slices
the first thing is actually to pick from where you would like to build your system. the part isn't a single service or multiple services, but a slice of system functionality. the slice is usually an end to end flow that represents a user's journey with the system. better if it encompass multiple services. there could be multiple slices that you can choose from. you can choose ont that is most simple or one that touches current system's pai points, and you would like to prove that the new architecture actually can help solve or reduce the pains.

### backlog and IPM

now we've decided the content of the first MVP for our new system. product manager will look into the slice, and snapE stories the slice consists of. the PM will start write the user stories, which is out of the scope for this post. when he is ready, the PM will summon the team to do the ritual of pre-IPM or IPM, so the team can look the story and vote for the score of the story. the score could be 0, 1, 2, 3 the fibonacci ones. the score should based on complexity of the story not simply the time needed. 


## xp and tdd



the iteration of parallelism and interleaving of backlog refinement and coding is the central part of software design processes. there'll be needs to re-visit the high level design but certainly it's significancy less so.

specifically, the testing code we can't emphasize enough is also the part of the design too. it's the validation part of design processes.

since all of these are designs, the manufacturing process is actually the CI/CD pipeline we created to help us get rid of this mundane labor, we all don't want to be the assembly line workers.
