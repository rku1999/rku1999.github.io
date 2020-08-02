---
layout: post
title: Puppeteer or the puppet?
date: 2020-08-02
categories: code
---

During my internship, I was tasked with creating a tool that automatically screenshots relevant ads on specific web pages. This tool will be mostly used by project or product managers. My project manager informed me that there is an existing version of this tool written by a former employee. However, there were some downsides to the version he had written. To begin with, he wrote it in JavaScript and required the project or product managers, some of whom are not very savvy with coding, to edit the code each time they want to run it on a different web page and then run it in a terminal. Then, the first version also appended each screenshot to each other (for some reason) instead of saving it as a separate file, making it really hard to identify individual screenshots.
From here, I set out to create the tool that fixes these flaws and essentially making it easier for the project and product managers to use.

Since I was pretty familiar with the Selenium framework on Python, I thought I would continue to utilize it for this project. However, I later realized that it was impossible to look for the ads by simply identifying and grabbing DOM elements with Selenium's `driver.find_elements_by...`. This is because each web page displays their ads differently and therefore their HTML is written and organized differently. Therefore I cannot simply look for a constant tag or class or any sort of identifier to find the ad. Instead, I will have to parse through all the requests sent from the web page and see if any of them include the server domain from which the ads of interest are originated. At this point, I feared that Selenium wouldn't have a built-in method that allows me to intercept the outgoing requests of a web page.

And alas, I was correct.

So, I decided to dig through the old repo and checkout how the magic is done in the JavaScript version. It turns out he utilized a library called Puppeteer, which is a Node library that provides a high-level API to control Chrome or Chromium over the DevTools Protocol. Fortunately, there is an unofficial Python port of puppeteer called Pyppeteer that I am able to use for this project. 

In the end, I was able to utilize the Pyppeteer library and Tkinter to build a Python application that successfully carries out the tasks while still being very easy to use for the project managers.
