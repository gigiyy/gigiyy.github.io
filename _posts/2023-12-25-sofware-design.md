---
layout: post
title: software design with swift method and XP/TDD
categories: software design
tags: swiftMethod XP TDD
---

let's see how to implement the software design using swift method and XP.

## introduction

the software design I'm talking about here is related to what Jack W. Reeves talked about in his famous [essays](https://www.developerdotstar.com/mag/articles/reeves_design_main.html)

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
- events are those happens in and around the system of business value
- events should be written in past tense, one sticky for one event
- events should be arranged one after another in time elapse order from left to right. the events follows could be triggered by previous one, or just should happens next in logical order.


below is one of the example that shows how user register itself and optionally add payment method to their account.
![event storming](/assets/images/event-storming.png)

### service identification

### boris

### snapE

## backlog maintenance

### thin slices

### backlog and IPM

using swift method, you'll be able to complete first round in roughly 2 to 3 weeks, and start your detailed design in less than 4 weeks.

the iteration of parallelism and interleaving of backlog refinement and coding is the central part of software design processes. there'll be needs to re-visit the high level design but certainly it's significancy less so.

specifically, the testing code we can't emphasize enough is also the part of the design too. it's the validation part of design processes.

since all of these are designs, the manufacturing process is actually the CI/CD pipeline we created to help us get rid of this mundane labor, we all don't want to be the assembly line workers.

## xp and tdd

