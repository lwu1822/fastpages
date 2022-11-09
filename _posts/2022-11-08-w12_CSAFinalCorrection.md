---
toc: true
layout: post
description: AP CSA Finals Corrections
categories: [cb]
title: AP CSA Finals
comments: true
---

Below is my score on the Trimester 1 AP CSA Finals. My score is 35/40.

<img src="{{site.baseurl}}/images/w12_CSATri1FinalScore.jpg" alt="Trimester 1 AP CSP Finals Score" >

<br>

These were the questions that I got wrong: 

<img src="{{site.baseurl}}/images/w12_CSATri1FinalCorrection.jpg" alt="">

* Why I chose the wrong answer: I overlooked the word **always** in the question, which was why I also selected 1 as the correct answer (since if data does not contain 5, there would be an error). 

* What I learned: Since the question says **always**, 1 would not be correct because if the one element in `data` is 5, there would not be an error. 

<br>

<img src="{{site.baseurl}}/images/w12_CSATri1FinalCorrection3.jpg" alt="">

* Why I chose the wrong answer: I mistakenly believed that `Math.random()` produced a number between 0 and 1, inclusive. I also failed to realize that choice A could return an index of -1, which would produce an error. 

* What I learned: `Math.random()` produces a random number between 0 and 1, but not including 1. Furthermore, the `(int)` type conversion does not round; therefore, `myList.size()` multiplied by a random decimal number will always result in a product less than `myList.size()` by at least 1, which will be enough for the maximum index number, which is always 1 less than the size of the list. 

<br>

<img src="{{site.baseurl}}/images/w12_CSATri1FinalCorrection2.jpg" alt="">

* Why I chose the wrong answer: I was not familiar with the `.add` method. I was actually on the right track; however, when I went through the for loop the first time, I assumed that `baboon` would always be at index of 1, leading me to choose D instead of B. 

* What I learned: Make sure to iterate through the entire for loop until the condition is false. 

<br>

<img src="{{site.baseurl}}/images/w12_CSATri1FinalCorrection4.jpg" alt="">

* Why I chose the wrong answer: I did not understand that both the reference parameter and the actual parameter are aliases. 

* What I learned: Passing a reference parameter results in it and the actual parameter being aliases to the same object. Therefore, changes made in the `mystery` method will also appear in `values`. Replacing the element of one index after the current index with the sum of the element in the current and subsequent index will result in the answer choice of C. 

<br>

<img src="{{site.baseurl}}/images/w12_CSATri1FinalCorrection5.jpg" alt="">

* Why I chose the wrong answer: I forgot to check the second part of the OR conditional, where `k<4`.

* What I learned: Since `k` is always less than 4, there would be an infinite loop. 