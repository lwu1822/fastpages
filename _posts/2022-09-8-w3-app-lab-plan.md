---
toc: true
layout: post
description: App Lab Planning
categories: [code.org]
title: App Lab Plan
comments: true
---

Here is the [link](https://studio.code.org/projects/applab/dbyn_t-_ioCVUC9PB3UiDjg0mKNmHCLnMy0F5ND1uRY) to my app. 

## Subject

Since I'm in AP Stats, I decided to create a statistics quiz. 

## Questions
1. What is the mean of the following set of numbers: 5, 8, 9, 15, 16?
2. Normal distribution picture: What percent of data lies between one standard deviation of the mean?
3. A class of 30 students were surveyed on how many hours they sleep. The average was 7 hours with a standard deviation of 1.5 hours. What percentage of students sleep less than 8 hours? 

## Initial planning with partner

Shreyas and I planned out a general format for how we would make our individual apps. 

We planned out four stages to make the app: design, brainstorm, implementation, and finishing.

We both created quizzes with three questions. Some of the code that we planned on excessive use was the `onEvent` function, which allowed an action to happen, such as switching the screen, given that something has occured, such as the click of a button.

## Design
My app consists of six screens: Homepage, questions 1-3, end screen, and a finish screen. 

Below are some pictures of what the initial design looked like:

<img src="https://lwu1822.github.io/CSP-fastpages/images/w3AppLabPlan-appLabOriginalText.jpg" alt="Original homepage" width="143" height="200">

<img src="https://lwu1822.github.io/CSP-fastpages/images/w3AppLabPlan-appLabOriginalAnswer.jpg" alt="Original text" width="140" height="179">

After the initial design, I made a few revisions, namely changing the font, adding buttons (originally, the user had to click the screen), and adding radio buttons for the multiple choice selection. 

An intermediate photo where I added a button: 

<img src="https://lwu1822.github.io/CSP-fastpages/images/w3AppLabPlan-appLabButtonChange.jpg" alt="Button added" width="149" height="207">

One of my screens on the final design: 

<img src="https://lwu1822.github.io/CSP-fastpages/images/w3AppLabPlan-appLabFontChange.jpg" alt="Original text" width="138" height="210">


## Coding

My code is relatively simple. A majority of the code used the `onEvent` function. I used the function for two purposes, the first was to change the screen when the Next button was pressed, and the second was to increase the score if the correct multiple choice was selected. 

<br>

Something else I made additionally was the use of a list that recorded if the user answered each individual question correctly. At the end of the quiz, the person would be able to receive feedback on what they answered correctly and anything that they could improve on, if needed. 

I accomplished this by creating a list with the name of `questionRight`. The index of the array corresponded to the question, so if the user answered correctly on the first question, `questionRight[0]` would have a value of 1. At the end of the quiz, the questions that had a value of 1 would have a congratulations message, and the questions that had a value of 0 (incorrect) would have an explanation on how to arrive at the correct answer.

### Explanations of code

This is a screenshot of part of my code. The rest of my code followed basically the same format. If you wish to check out my code, you can do so [here](https://studio.code.org/projects/applab/dbyn_t-_ioCVUC9PB3UiDjg0mKNmHCLnMy0F5ND1uRY/view).

<img src="https://lwu1822.github.io/CSP-fastpages/images/w3AppLabPlan-appLabCode.jpg" alt="My AppLab code">

Here's how the code works: 

The first block of code is an `onEvent` function, in which when the next button (`q1ButtonNext`) was pressed, the app screen will change to the next question (`q2Screen`).

The second block of code is another `onEvent` function. This time though, when choice B is selected (`q1ButtonB`), a predefined variable `score` will increase by 1. 

<br>

Now I'll give an overview on the use of a list in my app. First, I created a list called questionRight that contains three elements, each with the value 0.

<img src="https://lwu1822.github.io/CSP-fastpages/images/w3AppLabPlan-listCode.jpg" alt="List code">

Later on in the code, if the user selects the correct answer choice for the button, the value of the element would become 1. 

<img src="https://lwu1822.github.io/CSP-fastpages/images/w3AppLabPlan-indexCode.jpg" alt="Index code">

At the end of the code, I used an `if-else` statement to decide which feedback message to show. If the element of the index is 0, the feedback for the wrong answer would be show; otherwise, the feedback, for the correct message would show.

<img src="https://lwu1822.github.io/CSP-fastpages/images/w3AppLabPlan-feedbackCode.jpg" alt="Feedback code">

I could use individual variables in the code, but I used a list partially in preparation for the AP CSP Create Task. I think using a list would help in that if the quiz had more questions, using a list would be more organized than creating an individual variable for each question.


### Things I learned

The code I encountered in AppLab was new to me. I used the documentation [^1] very frequently.

I had to learn most of the things I coded. The most important code that I learned was the `onEvent` function. You can use it to specify an action to do when a certain event occurs, such as the press of a button. 


[^1]: [Documentation 1](https://studio.code.org/docs/ide/applab/expressions/button) and [2](https://studio.code.org/docs/concepts/)