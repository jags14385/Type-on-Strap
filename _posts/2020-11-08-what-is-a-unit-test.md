---
layout: post
title: What is a Unit Test
date: 2020-11-08
---

A test which asserts a " UNIT " is a Unit Test.

In the OOPS world, the unit has usually been a class. Hence, we have had, unit tests which pertain to a per class.

The general attributes of such tests are :

- Their runtime is in milliseconds or at max in seconds
- They are self contained
- They are idempotent i.e they do not change the state of the app or environment,when run
- They can run in parallel with other Unit tests
- They are atomic nature i.e. they usually check for one thing per test. If there are trivial enough checks, it can be lumped into one unit test
