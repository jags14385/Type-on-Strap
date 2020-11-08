---
layout: post
title: What is a Unit Test
date: 2020-11-08
---

A test which asserts a "UNIT" is a Unit Test.

In the OOPS world, the unit has usually been a class. Hence, we have unit tests which pertain to a per class.

The general attributes of such tests are :

- They are easy to run with minimal setup
- Their execution runtime is in milliseconds or at max in seconds
- They are self-contained
- On execution, they do not change the state of the app or environment
- They can run in parallel with other unit tests
- They check for one thing per test. Can be grouped into one tests for more than one trivial check

With the characteristics defined, let's talk about it, in the context of 
[Serverless](https://en.wikipedia.org/wiki/Serverless_computing).

How would one write tests to test an API, which does only one thing ?? For example, an API which returns the records of an employee from DB with the provided search parameter.

Questions:
 - How does a unit test (in its traditional definition) look?
 - How does an integration test look?
 - Is there an overlap? Do we need both kinds of tests for the problem at hand?
 - How to approach this problem

We can begin exploring this, by reading [Martin Fowler's take on [Solitary vs Sociable unit tests](https://www.martinfowler.com/bliki/UnitTest.html). 
 
 I prefer talking to DB and getting back a response. Let's explore this approach further. You have spun up a DB using [Docker](https://www.docker.com/) and have well-defined migration steps created and automated.