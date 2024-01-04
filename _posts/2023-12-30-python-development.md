---
layout: post
title: python development environment setup
categories: python
---

the trick is to use `pyenv` and `venv` at the same time.

first install `pyenv`
```bash
brew install pyenv
```
with it, you can install the python versions you needed.
```bash
pyenv --list
pyenv install 3.12.1
pyenv install 3.10.13
pyenv install --list
```
add `.python-version` file to your project directory.
```text
3.10.13
```
for this to work you need to add below line to your `.bash_profile`:
```bash
eval "$(pyenv init -)"
```
now can start using `venv` to install all the packages that specific to your project:
```bash
python -m venv .venv
. .venv/bin/activate
...
deactivate
```