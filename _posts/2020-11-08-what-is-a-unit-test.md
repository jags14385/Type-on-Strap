---
layout: post
title: What is a Unit Test
date: 2020-11-08
---

A test which asserts a "UNIT" is a Unit Test.

In the [OOPS world](https://en.wikipedia.org/wiki/Object-oriented_programming), the unit has usually been a class. Hence, we have unit tests which pertain to a per class.

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
 
I prefer talking to the database and getting back a response. Let's explore this approach further. You have spun up a database using [Docker](https://www.docker.com/) and have well-defined migration steps created and automated. Because of this setup, I can parallelize the execution of my test cases. This approach allows not to have Mocks or Stubs or Test Doubles for any my requirements. Let's evaluate its Pros & Cons.

This talks to a DB. Hence Bad !!!. This is not true. The environment, I am talking to against is clean and I have absolute control over it. How many calls will you make in parallel (twenty at max, I presume)? Also, my tests are deterministic. I know, exactly, what data is present and what I can expect out of it. The whole test run, will run, under a minute.

It blurs the boundary between a Unit test and Integration test, which is fine, for the scope of work (UNIT). The development practices that I adhere has allowed me to do this. You do not need to have two different sets of tests in this case. One set of test cases are functioning as both UNIT and Integration test cases. For a hosted environment, all that changes is the config and nothing else.

How would you check for contract testing, where other APIs have to interact with the Employee API and vice versa. The answer is Docker Images. I am using the dockerized version of the Employee API as a dependency for other APIs to consume and vice versa. It gives me the confidence to say `Employee API works fine with Version X of other APIs`. It helps with the independent deployment of the Employee API and other APIs.

From this, we can come to an informed conclusion that, for a well-defined scope of work or UNIT, with well-defined development practices, the proverbial scope of Unit and Integration tests will merge. Depending on what you are testing for, the feedback loop will be super fast. The guidelines with which the original Unit tests targeted are still intact.

Thanks for taking the time to read this.
You can tweet to me @vaiuntj for feedback.