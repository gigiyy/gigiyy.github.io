---
layout: post
title: Swift Method - Revolutionizing Legacy Modernization
categories: software design
date: 2024-01-29
tags: swiftMethod XP TDD
---

Swift method is the methodology pivotal for development teams embarking on the journey of modernizing their legacy systems into contemporary microservices architectures. This approach seamlessly integrates with Extreme Programming (XP) and Test-Driven Design (TDD), methodologies gaining recent popularity.

## Introduction

> "we are doing DDD without mention it to our customer."
>
> <p style="text-align: center;">--Shaun Anderson</p>

In the realm of software design, debates have surged over delineating what constitutes design within the software development process. It is highly recommended to delve into the seminal essays by Jack W. Reeves on this subject [here](https://www.developerdotstar.com/mag/articles/reeves_design_main.html).

While traditional notions confine design to architects or senior developers, diverse team members contribute to the design process in unique ways. For instance, when a product manager prioritizes feature development, envisioning initial business value for end-users, it embodies a form of software design. Similarly, a designer crafting intricate interaction blueprints or a developer meticulously scripting unit tests while envisaging system behavior in varied scenarios, actively participates in software design, albeit focusing on distinct facets.

I categorize the notional architecture design process (Swift Method) as high-level design, while selecting thin slices and maintaining backlogs as mid-level design. The coding phase, executed in a Red-Green-Refactor cycle, constitutes detailed design.

Subsequent processes, such as setting up CI/CD pipelines, form part of the building process but lie outside the realm of design.

The Swift Method, conceptualized by Shaun Anderson, former Pivot, is extensively detailed on his personal site [here](https://www.swiftbird.us/the-swift-method). Additionally, a talk presented at the Explore DDD conference is accessible [here](https://youtu.be/7-fRtd8LUwA?si=06U1JYT-34fYJKOC).

For XP and TDD, abundant resources exist, including dedicated sites [like this](http://www.extremeprogramming.org/) and the foundational book by Kent Beck, available [here](https://a.co/d/6RMzF9I).

## Swift Method

The Swift Method, depending on its flavor, may take anywhere from half a week to 3 weeks.

The process I'll outline here took longer to complete; however, it might be more practical for beginners to follow.


### Goals and Anti-Goals

Although seemingly obvious, setting clear, prioritized goals and delineating what isn't a high priority, at least for the present, holds paramount importance for the project team.

Especially in enablement engagements lasting only 6 to 12 weeks, it's crucial to emphasize that implementing the system in its entirety isn't our primary goal (an anti-goal). Conversely, if focusing on the enablement aspect, we further define which aspects matter most for the team. Typically, project core members might present divergent objectives, necessitating grouping them into several themes and prioritizing them accordingly.

### Event Storming

Event storming entails gathering the business events occurring in and around the target system. This activity, a simplified version of Alberto Brandolini's [event storming workshop](https://www.eventstorming.com/), embodies several important points:

- Events are occurrences within and around the system with business value.
- Events are written in the past tense, one sticky note per event.
- Events are arranged in chronological order from left to right, following logical time progression.

Below is an example illustrating how a user registers and optionally adds a payment method to their account.
![Event Storming - Bird's Eye View of the System](/assets/images/event-storming.png)

### Service Identification

After identifying events, our aim is usually to collect 60 to 80 percent of the business events within the system on the board. It's vital not to aim for all events, particularly trivial ones, unless there are issues or performance concerns in that part of the system.

To identify potential service candidates, we evaluate internal events individually, considering the business capability necessary to enable each event. Guidelines for identifying candidates include:

- Business capabilities
- Data ownership
- Loosely coupled
- Testability

When in doubt, specific criteria help determine [whether it should be a microservice](https://tanzu.vmware.com/content/blog/should-that-be-a-microservice-keep-these-six-factors-in-mind). Excerpts ine below:

- Rate of change
- Scalability (independently)
- Lifecycle management
- Isolated failure
- Simplifying external dependencies
- Freedom of choosing other technology

Here's an example of the service identification results for the events collected earlier.
![Service Identification](/assets/images/service-identification.png)

### Boris

The Boris process is pivotal in the Swift Method. Here, we map relationships between service candidates based on those event flows identified in previous steps, utilizing abstracted communication methods (synchronous or asynchronous). Communication protocols beyond our control are usually marked in black and set aside.

Here's how you transform events into the first draft of a Boris diagram.
![The Beginning of Boris](/assets/images/boris-start.png)
When completed, the Boris resembles a spider web of the service system.
![Whole Boris - Spider Web of the Service System](/assets/images/boris-full.png)

### SnapE

The SnapE step, with its odd name standing for "snap not analysis paralysis extended," entails capturing the internals of each important service candidate used in our Boris diagram. By now, you should understand why we refer to them as potential service candidates, as they may change, combine, or split multiple times.

When most of the diagram is complete, capturing 60 to 80 percent of the flows during the event storming phase, we gain confidence that the system (notional) architecture has taken shape and won't change significantly.

It's then time to document the internals of services, capturing APIs, data, high-level stories, and risks. Here are two examples.
![SnapE - Profile of the Service](/assets/images/snape.png)

Thus far, this constitutes the first iteration of your Swift process. Though demanding (typically requiring full-time team involvement for the entire 4 weeks), compared to the traditional process, the Swift Method aptly matches its name.


## Backlog Maintenance

Once we've established the initial version of our notional architecture, is it time to don our developer hats and start coding? Not quite yet.

### Thin Slices

The foremost task is to select where to commence building our system. This segment isn't a single service or multiple services but rather a slice of system functionality. The slice typically represents an end-to-end flow embodying a user's interaction with the system. It's preferable if it spans multiple services. There may be multiple slices to choose from. Opt for one that is simplest or one that addresses current pain points in the system, aiming to demonstrate how the new architecture can alleviate or mitigate these pains.

### Backlog and IPM

Now that we've determined the content of the first Minimum Viable Product (MVP) for our new system, the product manager scrutinizes the slice and delineates the stories it comprises. The PM begins crafting user stories, a topic beyond the scope of this post. When ready, the PM convenes the team for the pre-IPM or IPM ritual, enabling the team to review the stories and assign a score. The score, using Fibonacci numbers such as 0, 1, 2, or 3, should reflect the complexity of the story rather than simply the time required.


## XP and TDD

Given the abundance of available materials, I'll forego delving into most details in this section.

However, one critical aspect the team should contemplate is the true essence of a unit test.

The original meaning of a unit test, contrary to common belief, pertains to a test that can run independently. It's unrelated to the scope or target it tests against, as commonly understood nowadays.

This raises another question: Consider a scenario where, during initial development, your unit test covers the behavior of accepting REST requests from users and inserting that data from request parameters into the database using the repository, which was a direct dependency of the controller class.

Later, you refactor out the repository dependency and transfer it to your service class. Should you refactor this unit test to align with the changes in your production code?

## Final Words

The aforementioned processes don't follow a linear trajectory from architecture design, development, to deployment. Instead, they represent an iteration of parallelism and interleaving of backlog refinement and coding processes. This constitutes the crux of software design processes. While high-level design revisitation is common, its significance diminishes.

Specifically, testing code, which cannot be emphasized enough, also constitutes part of the design. It's the validation aspect of design processes.

Given that all these are designs, the actual manufacturing process is the CI/CD pipeline we've established to alleviate us from mundane labor, sparing us from being mere assembly line workers.
