---
toc: true
layout: post
description: JavaScript Table
categories: [js]
title: Creating a table using JavaScript
comments: true
---
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>For Loop Animals</title>
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
    printFruits = new Combine(fruits);
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