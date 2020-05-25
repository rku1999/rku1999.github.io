---
layout: post
title: "Python Selenium Implicit Wait"
author: Ray
date: 2020-05-25
categories: blog
---

I am learning Python's unittest module in combination with Selenium to write an autotesting framework for a webpage at my internship. During the past few days, I wrote more than a dozen tests. Though it was solid progress, the sluggish runtime has driven me mad. After spending hours writing and rewriting my code to see what kind of god forbidden bug is butchering my runtime, my efforts was to no avail. So, I've decided to turn to the Selenium documentation.

And right there, RIGHT THERE, on the page about Waits:

> An implicit wait tells WebDriver to poll the DOM for a certain amount of time when trying to find any element (or elements) not immediately available. The default setting is 0. Once set, the implicit wait is set for the life of the WebDriver object.

Ok...so two things jumped out to me immediately:
1. Implicit wait, once set, applies whenever you're trying to find elements not immediately available.
2. Once set, implicit wait lives as long as the WebDriver object

After reading that, I immediately knew where I screwed up. When I first started using Selenium, I set an implicit wait of 30 seconds for some reason unbeknownst to me. And now, as you probably saw quite a while ago, that's what's causing most of my unit tests to take more than 30 seconds.

... I swear from now on I'm going to read documentations more thoroughly.
