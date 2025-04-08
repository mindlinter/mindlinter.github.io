---
layout: ../../layouts/post.astro
title: "TDD(BDD/ATDD) and AI"
pubDate: 2025-04-09
description: "The modern vibe coding is just a good old one BDD with modern tools."
author: ""
isPinned: true
excerpt: "The modern vibe coding is just a good old one BDD with modern tools."
image:
  src:
  alt:
tags: ["ai", "tdd", "bdd", "atdd", "vibe coding"]
---

How old are you? Do you remember TDD? Test Driven Development ring any bells? It was quite a popular extreme programming practice introduced by Kent Beck. The idea behind it is that if something is good let’s do it more, extremely more, and bring it to a completely new level. 

Testing is good. Automated tests are good. Unit tests are good. We can start to write tests **before** writing the code! What benefits does it have? The main benefit is that you write testable and 100% tests-covered code. And it works naturally as you initially write tests and only later the code. You never get the problem that it is hard to cover your code with unit tests.

It is a matter of habit. It is hard to force yourself to use TDD. You usually are focused on solving problems and want to write a bigger part of logic at once. But you should not! You should write the only code that fixes your tests. Do not think about the future! To solve this problem there are exercises, named katas. You work on imagined tasks to make the habit. Write test. Write the code to pass all tests, but not more. Refactor. Repeat.

I tried TDD on a few small projects. It was working in some kind. I got great test coverage, and the project was successful, but I had a feeling that it could be done much faster. And, to be honest, I cut the corners for some tasks. I just didn’t want to write code that would work to only fix the test, but I will need to remove it in the next iteration.

TDD never worked for me on a big project. I am trying to find a healthy balance between test coverage and effort. Not everything should be tested. It is still easier for me, to first write the code and later add the tests. However, sometimes it is valuable to write tests behind the code. It should not be the religion. Try everything, check if it works for you, and adopt it for yourself and use, when you think it is valuable.

ATDD — acceptance test-driven development. That is an attempt to make the tests be unified language not only for developers but also for testers and customers.
BDD — behavioral-driven development. The idea is to describe tests in domain terms. And cover logic with automated UI tests and integration tests.

You should get the polished project in the case of BDD in theory. But in reality, time and available resources make corrections. I used some kind of BDD only on one project, where excellence was the goal. It may feel like wasting time. You need to add one button. You write specifications in the special format, prepare the tests for it, and only then write the logic. And a week later you get the request to change the behavior. And you rewrite the specifications, tests, and code. And two weeks later … a change request, again. The major part of projects doesn’t need it to avoid huge implementation and maintenance costs. You get quality, test coverage, and documentation, but not for free.

That was a very long introduction to TDD/ATDD/BDD development methodologies. They are not very popular in 2025. I don’t see regular articles, videos, posts about them. TDD, ATDD, and BDD have been dying last few years. But I see posts about AI coding every day. I see huge hype around vibe coding. And that brings me to the idea that BDD is the dad of vibe coding, where the developer was replaced by AI. And, in theory, if you have quite a good BDD project, you should be able to remove the code and ask the AI to write this code.

I think that **AI will bring new life to TDD/ATDD/BDD practices**. It will make them much more efficient. Once you have a structured and well-defined behavior description, AI will help you speed up writing tests. Once you have tests in place, AI will speed up writing code.