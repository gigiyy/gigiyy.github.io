---
layout: post
title: design and build of software
---

work in progress

When it comes to software design, ongoing debates persist regarding its true definition within the software development process. It's highly recommended to explore the seminal essays by Jack W. Reeves on this subject, available [here](https://www.developerdotstar.com/mag/articles/reeves_design_main.html).

While traditional notions confine design to architects or senior developers, diverse team members contribute to the design process in unique ways. For instance, when a product manager prioritizes feature development, envisioning initial business value for end-users, it embodies a form of software design. Similarly, a designer crafting intricate interaction blueprints or a developer meticulously scripting unit tests while envisaging system behavior in varied scenarios, actively participates in software design, albeit focusing on distinct facets.

I would like to categorize the notional architecture design process (Swift Method) as high-level design, while selecting thin slices and maintaining backlogs as mid-level one. The coding phase, executed in a Red-Green-Refactor cycle, is the detailed version of it.

Subsequent processes, such as setting up CI/CD pipelines, form part of the building process but lie outside the realm of design.


Specifically, the testing code, which cannot be emphasized enough, also constitutes part of the software design. It's the validation aspect of design processes.

Given that all these are designs, the actual manufacturing process is the CI/CD pipeline we've established to alleviate us from mundane labor, sparing us from being mere assembly line workers.

Maybe we should call ourself designer too.