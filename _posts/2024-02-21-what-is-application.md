---
layout: post
title: what is application, anyway
categories: software design
---

When you inquire about the meaning of "application", you are bound to receive a variety of responses. For a DBA, it might be a specific Sybase installation, while from an operator, it might be one of the pods within the cluster, the cluster itself, or the Jenkins pipeline running on a bunch of VMs.

Developers, too, struggle to pin down a concise definition. Is it a reference management system? Perhaps the batches that is scheduled to run every new year's eve to change the Nengo through out the system? Because of this ambiguity, developers, who are good at naming, try to come up different terms like service, system, workload, pod, deployment and more.

And it become evident when it comes to the observability of an application. What truly matters for a particular application's observability? Is it actually relevant to monitor one of the server's CPU usage percentage? It could be important for other team members, however, I would like to know whether I've spun up too many instances and incurring excessive cost.

Ultimately, it's best to defer to our business stakeholders, to whom we are ultimately accountable. They might categorize applications that manage customer information, enable stock trading, streamline settlements etc.

Starting from this perspective, as application support/developer, I'm interested in knowing whether a customer has completed KYC check or if there are any pending overdue settlements? 

When assessing the health of my application, should I focus on failing Lambda functions, amber alerts for databases, or backlogged queues? While there are numerous monitoring consoles available, they are often organized around specific functionalities like Lambda or databases. This is very much like putting all controllers in one folder and repository in another, which annoys me the most, and same for clean architecture to that extent. Architect usually draw nice picture depicting the architecture of the application, however bring it to live on the platform proves challenging.

Hence, it falls upon developers to create tailored views for themselves and stakeholders, which was called reports, unfortunately it's generated in batched fashion. However there must be better solution available already.