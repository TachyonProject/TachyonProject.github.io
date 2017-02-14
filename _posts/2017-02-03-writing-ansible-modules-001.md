---
layout: post
title: Writing Ansible Modules Part 1 - Preparing Your Environment
comments: true
categories: ansible, modules, configuration management, software development, automated testing, code coverage, agile, tdd, bdd
---
This is part 1 of a series of articles. For other parts, see
[the introductory article](/2017/02/writing-ansible-modules-with-tests.html).


## Prerequisites
You'll need a few things handy before you can continue:

- Git branching basics. [Learn Git Branching](http://learngitbranching.js.org)
  is a great resource!

- Ansible 2.2 features a tech preview of Python 3 support.
- Ansible 2.3+ will enforce all code to be version compatible for both Python 2 && 3.

- Pip

- The following Python libraries:
    - paramiko
    - PyYAML
    - Jinja2
    - httplib2
    - six
    - nose

  - Basic testing knowledge including mocking. If you're not too familiar with mocking, you can still follow along but I encourage you to read up on it after you're done here as it will help make your unit tests more robust.


## Prep Your Ansible Repo
