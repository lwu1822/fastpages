---
toc: true
layout: post
description: JavaScript Table
categories: [js]
title: Creating a table using JavaScript
comments: true
---

{% include nav_frontend.html %}

<html>

<head>
    <meta charset="UTF-8">
    <style></style>
</head>

<body>
<div id="output_div"></div>
<script> 
    function Fruits(name, taste) {
    this.name = name;
    this.taste = taste;
    }
    <!-- space -->
    var fruits = [
        new Fruits("apple", "sweet, sour"),
        new Fruits("mango", "sweet")
    ];
    <!-- space -->
    function Combine(fruits) {
        this.fruits = fruits;
        this.combine = [];
        this.fruits.forEach(fruit => {this.combine.push(fruit);});
    }
    <!-- space -->
    var printFruits = new Combine(fruits);
    <!-- space -->
    var outputHTML = "";
    outputHTML += "<table>";
    outputHTML += "<tr>";
    outputHTML += "<td>" + "Fruit Type" + "</td>";
    outputHTML += "<td>" + "Taste" + "</td>";
    outputHTML += "</tr>";
    <!-- space -->
    var week = 0;
    for (var row of printFruits.combine) {
        outputHTML += "<tr>";
        outputHTML += "<td>" + row.name + "</td>";
        outputHTML += "<td>" + row.taste + "</td>";
        outputHTML += "</tr>";
    }
    outputHTML += "</table>";
    <!-- space -->
    document.getElementById("output_div").innerHTML = outputHTML;
</script>

</body>

</html>

Below is the code that I used to create the table above in JavaScript: 
```
<script> 
    function Fruits(name, taste) {
    this.name = name;
    this.taste = taste;
    }
    <!-- space -->
    var fruits = [
        new Fruits("apple", "sweet, sour"),
        new Fruits("mango", "sweet")
    ];
    <!-- space -->
    function Combine(fruits) {
        this.fruits = fruits;
        this.combine = [];
        this.fruits.forEach(fruit => {this.combine.push(fruit);});
    }
    <!-- space -->
    var printFruits = new Combine(fruits);
    <!-- space -->
    var outputHTML = "";
    outputHTML += "<table>";
    outputHTML += "<tr>";
    outputHTML += "<td>" + "Fruit Type" + "</td>";
    outputHTML += "<td>" + "Taste" + "</td>";
    outputHTML += "</tr>";
    <!-- space -->
    var week = 0;
    for (var row of printFruits.combine) {
        outputHTML += "<tr>";
        outputHTML += "<td>" + row.name + "</td>";
        outputHTML += "<td>" + row.taste + "</td>";
        outputHTML += "</tr>";
    }
    outputHTML += "</table>";
    <!-- space -->
    document.getElementById("output_div").innerHTML = outputHTML;
</script>
```

<br>

Explanation of code:

An object called `printFruits` is created. This calls the `Combine` constructor, which uses information from the `fruits` array, which calls the `Fruits` constructor. This creates a key of `name` and `taste` and a value as set by the code. 

Now, what does `this.fruits.forEach(fruit => {this.combine.push(fruit);});` do? Understanding the arrow function (`=>`) took me awhile, but this is basically a shorthand way to write:
```
this.fruits.forEach(function(fruit) {
    this.combine.push(fruit);
});
```
which basically adds the elements in the fruit array into a new array called `combine`. 

Afterwards, a table is created using HTML within JavaScript. The for loop loops over the `combine` array and outputs it as HTML in the table. 

And that's it! A table made in JavaScript. 