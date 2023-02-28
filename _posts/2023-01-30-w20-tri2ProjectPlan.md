---
toc: true
layout: post
description: 
categories: [misc]
title: AP CSP Trimester 2 Project Plan
comments: true
---

The project that I will make for MyToolkit is MyClasses, a feature that can allow students to search for classes and see others' review of them. 

## CollegeBoard Criteria

**Program Purpose and Function**: The purpose of the program is to help students in their course selection process. The function will be to let the student search for the class that they are interested in taking and show a list of reviews that other students have left for the class. Input will be the class that the student searches for and output will be the reviews for that class.

**Data Abstraction**: In my search feature, I created a list with possible class names. The name of my list is `dnClasses`, and the data in the list is all of the class names. This allows the search to find if the class that the student inputs exists or not, and also allows the program to see if the class that the student entered matches to the class in the list without regard to case. By ensuring that the class that the student entered is valid, the program can proceed to find class reviews on the backend and allow the student to view the reviews that they wish to see.


<img src="{{site.baseurl}}/images/list.jpg">

<img src="{{site.baseurl}}/images/list2.jpg">

**Managing complexity**: The list stores all of the classes at Del Norte. This manages complexity because the program can search through the list to see if one of the classes matches the one that the student enters. Without the list, each class name would have to be stored in a variable and individually compared with the class that the student enters.

**Proceduaral Abstraction**: The function name is `findClass(classInput)`. This contributes to the functionality of the program by deciding if the program should get data of the class that the student inputted on the backend or if it should output an error message. 

<img src="{{site.baseurl}}/images/algorithm.jpg">

**Algorithm Implementation**: The function name is `findClass(classInput)`. The function takes in the name of the class that the student is searching for, and repeatedly compares it to the class names in the `dnClasses` list to see if one of the lists matches (iteration). If there is a match (selection), the `classFound` boolean variable is set to true. This way, if the class was not found, an error message could be displayed in HTML on the website. Otherwise, if the class was found, the next function, `getClassData`, would be called.

**Testing**: The two calls are `findClass("AP Biology")` and `findClass("test")`. The first call sends a valid class name, AP Biology. Therefore, the first section of the code is executed and the variable `classFound` is set to true. The second call sends an invalid class name. `classFound` is false, and an error message is displayed on the screen.

<br>

The theme of our project is school. Our website consists of features that include a login, an area where the students can input their schedules, gpa, class reviews, and tasks.

<br>

The parts that I worked on was the **class review**

In the sections below, I will document what I did to create these features and some interesting things that I learned.

# Create

The first section is the submit review. Students can enter in a class name, difficulty, hours of homework, days between tests, memorization level, and comments.


<img src="{{site.baseurl}}/images/create.jpg">

This sends a fetch request using POST to the backend. On the backend, I have an API endpoint called `CreateClassReview`. This endpoint takes in the body, which includes the username, class name, etc., and creates a `ClassReview` object and adds it into the database.

# Read

This is the place where the student can search for a class review. On the frontend, the class that the student searches for is taken in as a variable. This variable is used to query for the class reviews that are fetched from the backend. All classes are returned from the backend; however, on the frontend, the program searches through each class name until it finds a matches.

# Update

My update review consists of a section where students can edit their reviews. On the backend, the code is basically the same as my create endpoint. However, I call the `update()` method instead of `create()`, which saves the same object instead of creating a new object.

# Delete

Students can also delete a class review. On the backend, the program takes in the username and class name, searches for the specific database entry that corresponds to the students' input, and then calls the `delete()` method.