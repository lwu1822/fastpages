---
toc: true
layout: post
description: CSP Project Planning
categories: [CSP]
title: CSP Project Planning
comments: true
---

# Our Aim

We want to prioritize the customer before anything else; here's how this will be done:
1. Our website will run smoothly with minimal errors
2. Try to keep our website as engaging as possible
3. Listen to reviews and make changes as necessary
4. Make the results accurate

# About the Project

In this project, we are making a reverse dictionary. We were inspired by many students' studious and driven culture and wanted to create a site that could help them. A problem that we noticed among many students, especially those in advanced English courses, is that they often don't know or can't remember the word they want to use. Through the use of this website, we want to help these students allowing them to do well where ever they choose to use this website.

# How is This Done

In order to achieve this, we first need to get a basic understanding of how reverse dictionaries work and how to code them. After searching on Google, we came across many fascinating sites, some even explaining the basics of a reverse dictionary. Essentially it is looking for an output similar to the combination of the inputs. One of our ideas was to make the user input either the definition of the word or other words related to the word they need. For example, if you're searching for the word "apple," you can input "fruit," "red," and "grows on trees" to get your result. And currently, we are planning to code most of this with Python, use HTML to display everything, and use JavaScript to allow the user to interact with the results.

## Create Performance Task Categories

### 1 Program Purpose and Function
See above 

### 2  Abstraction
Each synonym could be stored in a list, which would either be manually created by us (less likely), or given in the API (more likely). The hard part would be to find a reverse dictionary API.

### Managing Complexity
By using a list to store the synonyms of words, the code would be simplified so that multiple variables, each storing only one word, would not be needed. 

### 4 Procedural Abstraction
We could make functions that include that collect the user's inputs of various word definitions. These inputs would then need to be processed by comparing with the information in the API and then being able to output the ideal words to frontend.

### 5 Algorithm Implementation
Recursion can be used to repeatedly find definitions that contain certain keywords that the user implemented. `if` statements could be used to select the words with the closest definition and display them under a category, then select the words with a moderate level of closeness and put them in another category. 

### 6 Testing
Many parts of the program would include the need for testing. First of all, we need to implement an API and connect the frontend with the backend so that the frontend can display information about the API. This would require testing by inputting many definitions and seeing if the outcome word is what is desired. 

# Team Scrum Board

[Team Scrum Board](https://github.com/users/lwu1822/projects/1)


# Agile Methodology Diagram

![]({{ site.baseurl }}/images/w5_CSPProjectPlanning-agile.jpg)
<br>

Our team used Slack as a form of communication to plan out our project.

![]({{ site.baseurl }}/images/w5_CSPProjectPlanning-teamTalk.jpg)
