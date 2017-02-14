---
layout: post
title: My Python Development setup
comments: true
categories: software development, continuous testing, automated testing, code coverage, agile, tdd, bdd, python
---

My work mainly includes coding in python.
While i choose certain elements over the rest, certain methodologies are extremely important to follow.
Here's what I have / use so far.

## TDD
Testing is a lot like seatbelts while riding a car.
you shouldn't feel safe without it.
So mastering a testing framework is always top priority.

My preferance is [tox](https://tox.readthedocs.io/en/latest/).

[Nose](https://nose.readthedocs.org/en/latest/) is also on the list, though it may have lost favor in some opensource communities. Its heavily used by the Ansible Community though.

Some things to note in the above are the following:

* As per [OpenStack coding guidelines](http://docs.openstack.org/developer/hacking/), imports should be segmented into three parts when necessary: imports from stdlib, imports from third-party libs, and finally imports within the project.
* PEP8 spacing is followed. Later in this article I will show how PEP8 compliance is automatically checked.

## Continuous Testing

Continuous testing is a very important part of a development workflow and is, I would say, at the same level of importance as continuous integration.
For Python, I came across [sniffer](https://pypi.python.org/pypi/sniffer) which supported nose out of the box but was configurable enough to run testr and friends too.

With gitlab / git / bitbucket you can implement various forms of automated runners (Travis, pipelines et al).
These DSLs require some learning, but definitely worth the effort.

## Monitoring Code Coverage

I found [coverage](https://pypi.python.org/pypi/coverage) which well adopted, and used most places I've seen doing coverage tests.

## Summary

I've gotten so used to continuous testing on my local environment that coding without it feels like driving without seatbelts.
It's really good to know that Python is as feature rich in this regard as most other languages.
