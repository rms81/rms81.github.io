---
layout: post
title: "The path to unit testing"
date: "2015-09-16 07:48:38 +0100"
comments: false
excerpt: "...Forget the 'right' way. Just keep in mind the problems that unit testing is trying to solve. Focus on the 'why' and not so much on the 'how'."
---

Since I started writing software, one of my main focus has been to constantly improve the quality of the code that I produce and consistently optimize the process of writing a clean and maintainable code. With that in mind I try to keep track of the proposed best practices and apply them whenever they apply. Some of the steps towards the goal of writing quality code have been more challenging than others, and I have to admit that, so far, one of the most challenging has been the adoption of unit testing.

Although I almost immediately realized how useful unit testing is, I can’t say that it has been an easy path.

In unit testing, like in most areas of software development, everything is very dynamic… There’s tons of different ways of doing it, and lots of frameworks to help you do it. Then there’s TDD, BDD, unit and integration tests. And to make things even more challenging, it seems that everybody has a different way of structuring and organizing things… But although not an easy path, it's undoubtedly one that's worthy. You probably won't start collecting the benefits right away, and it will be frustrating. Very often I felt that I was just wasting valuable time, because apparently things are never structured well enough, code coverage is never good enough…

So, my advice here is… Forget the “right” way. Just keep in mind the problems that unit testing is trying to solve. Focus on the "why" and not so much on the "how". Writing good and well structured unit tests isn't easy. You will fail, you will write useless tests, and tests that don’t test what they should… Don’t give up, it will get better. ;)

I’ve been trying to fully adopt unit testing for about two years. Every project I started has unit tests… But, only now I think that I’m starting to get more comfortable with it.

I´m in the early development stages of a big project, and for the first time I´m fully integrating the unit tests in the process… For every function I write, I’m writing unit tests, almost always in parallel. Sometimes even before… (Wow, look at me I’m doing TDD!! ) The benefits for integrating unit testing in the development process from the very beginning of the project are massive.

As I see it, one of the biggest advantages of writing tests immediately is that I can immediately spot problems in my API. Being immediately put in the role of the API consumer you can immediately see what does and doesn’t make sense and make the required changes… Which you can do knowing that as long as your tests are green you are not breaking anything…

On top of that, you will spend far less time testing the functionality of your application, since you don’t have to execute it to test. You can test just part of it in isolation.

Unit tests are also a good way of documenting the code, since your are showing how it’s meant to be used.

So, with all these ideas in mind… Don’t forget your unit tests, they will make your life easier.
