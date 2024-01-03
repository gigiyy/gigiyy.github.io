---
layout: post
title: install jupyter plugins with docker
date: 2024-01-03
categories: jupyter
---

first, install the needed plugin using jupyter UI when it's running in docker.

for e.g., the spell checker plugin `jupyterlab-contrib-spellchecker`.

next, use docker commit command to save the image:
```bash
docker commit CONTAINER_ID jupyter/scipy-notebook:new-tag
```

then modify the tag name inside the `notebook` script that were shown in [previous post]({% post_url 2023-08-12-start-jupyter-orbstack%})