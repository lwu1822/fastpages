---
toc: true
layout: post
description: i have been successfully frustrated
categories: [backend]
title: Java Backend Deployment
comments: true
---

# Crime News API

![]({{ site.baseurl }}/images/w6_javaBackendAPI-crimeTable.jpg "World Crime News from RapidAPI")


# How I created a table in Java backend using an API 

This took me a whole day to figure out. 

Learning about APIs is still an ongoing process for me, so below, I'll document the things that I learned about APIs and what I picked up while coding. 

The code that I started with was what I took from the RapidAPI website. I then used some code to parse the JSON response. This was the place that messed me up for a long time, as I kept receiving errors in my code. After hours of googling, I finally found the answer, and that fixed things up. 

However, the most important things I learned was:
1. The API calling process in Java
2. Thymeleaf

## API calling process in Java

First, an HTTP client needs to be created with `HttpClient`. Next, a request using `HttpRequest` is created to send a request to the HTTP client. Within the request, the type of request (GET), URI, and headers are specified. Putting it all together is `build()`. Then use the `client` to send back the HTTP request. 

## Thymeleaf

After receiving the JSON data, an issue that I ran into was to output the data into a table format on the frontend of Spring boot. I took a look at some of the programs already present in the spring portfolio, such as `greet.html`, knowing that it would have to convert backend data to frontend. Within the program, I noticed an interesting snippet of code which was `${name}`. Googling the syntax lead me to learn about Thymeleaf, which is a Java template engine. This was really cool, because Thymeleaf changes Java data into HTML (which can actually be shown on a webpage). I'll probably bore you with the details later when I update this blog further, but for now, you are spared :) Anyways, a simple Youtube search of "what is Thymeleaf" gave me an introduction of how to use this template language. The thing that was super useful that I learned from the video was that Thymeleaf uses `th:each` to iterate over arrays and lists. This allowed me to print the JSON data, which consisted of objects, into a table format. 