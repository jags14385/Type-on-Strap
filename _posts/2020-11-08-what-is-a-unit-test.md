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

With the characteristics defined, let's talk about it, in the context of 
[Serverless](https://en.wikipedia.org/wiki/Serverless_computing).

Context : How would one write tests to test an API, which does only one thing ?? E.g.: Query the records of an employee with the provided search parameter

Questions:
 - What does a unit test (in its traditional definition) look like ?
 - What does a integration test look like ?
 - Is there an overlap ? Do we need both kind of tests for the problem at hand ?