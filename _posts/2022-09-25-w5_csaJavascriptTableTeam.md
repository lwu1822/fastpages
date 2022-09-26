---
toc: true
layout: post
description: JavaScript Table for CSA Team Project
categories: [js]
title: Creating a table using JavaScript for the CSA Team Project
comments: true
---
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <style></style>
</head>

<body>
<div id="output_div"></div>
<script> 
    function TeamMembers(name, age, role) {
    this.name = name;
    this.age = age;
    this.role = role;
    }
    <!-- space -->
    var team = [
        new TeamMembers("Vidhi Kulkarni", 16, "Scrum Master"),
        new TeamMembers("Lily Wu", 16, "DevOps"),
        new TeamMembers("Riya Patil", 16, "Frontend"),
        new TeamMembers("William Wu", 16, "Backend")
    ];
    <!-- space -->
    function Combine(team) {
        this.team = team;
        this.combine = [];
        this.team.forEach(people => {this.combine.push(people);});
    }
    <!-- space -->
    printTeam = new Combine(team);
    <!-- space -->
    var outputHTML = "";
    outputHTML += "<table>";
    outputHTML += "<tr>";
    outputHTML += "<td>" + "Fruit Type" + "</td>";
    outputHTML += "<td>" + "Age" + "</td>";
    outputHTML += "<td>" + "Role" + "</td>";
    outputHTML += "</tr>";
    <!-- space -->
    var week = 0;
    for (var row of printTeam.combine) {
        outputHTML += "<tr>";
        outputHTML += "<td>" + row.name + "</td>";
        outputHTML += "<td>" + row.age + "</td>";
        outputHTML += "<td>" + row.role + "</td>";
        outputHTML += "</tr>";
    }
    outputHTML += "</table>";
    <!-- space -->
    document.getElementById("output_div").innerHTML = outputHTML;
</script>

</body>

</html>