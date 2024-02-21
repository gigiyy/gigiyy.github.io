---
layout: post
title: What a developer wants?
categories: software design
---

As I read Joel's post on the [developer abstraction layer](https://www.joelonsoftware.com/2006/04/11/the-development-abstraction-layer-2/), it struck me that this is what have been bugging me for the past few years.

Having been a developer for 23 years, I've often pondered what it takes to excel in my role. What are the keys to becoming a better developer?

It's not just about mastering programming languages or frameworks. It's about understanding the business requirements – a lump sum term that I use for everything other than coding.

This involves understanding stuff such as:

- The nuanced details that dictate whether I should print "Hello world!" or "Hello, Mr. Zhu."
- Familiarity with external systems and how to effectively communicate with them, including the teams responsible for those systems.
- Knowing the intricacies of pipelines that determine how my code transforms into a functional binaries.
- Navigating through the various gates necessitated by the policy.
- Understanding the infrastructure landscape that dictates where my application can be deployed.

As Developer, I would love the developer platform that can minimize the overhead that caused by these aspects, particularly on those last three bullet points. It would be wonderful If it can also make the second easier.

It may seem like a surprisingly short list, especially for developers who typically crave more memory, powerful CPUs, or GPUs.

But what if I told you that the "developers" here is not just the coders on your team? It also referring to those who support the programmers. No, I'm not referring to HR, Sales, DBAs who critique your SQL queries, or platform operators who handle server restarts.

In this context, "developers" encompass the entire team collaborating to deliver the software product. This includes the product manager who knows what business wants, designer who knows what end user wants and of course,  programmer who knows how to make it work.

What about the architect who often basks in the glory bestowed upon them by management? They're integral members of the development team, contributing to decisions like whether to implement a feature using a Lambda function instead of an EC2 application and storing the results in DynamoDB rather than RDS. You might appreciate the term "Anchor," previously used by Pivotal Labs, to describe individuals actively involved in making such decisions for the team.
