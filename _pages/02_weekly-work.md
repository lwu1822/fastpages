---
layout: page
title: Weekly Work
permalink: /weekly-work/
---


<table>
    <tr>
        <th>Week</th>
        <th>Assignments</th>
    </tr>
    
    
    {% for i in (0..3) %}
    <tr>
        <td>{{ i }}</td>
        {% if i == 0 %}
            <td><a href="https://lwu1822.github.io/fastpages/markdown/2022/08/19/post-1.html">First post</a> <br> <a href="https://lwu1822.github.io/fastpages/2022/08/20/java.html">Java</a> <br> <a href="https://lwu1822.github.io/fastpages/2022/08/20/python.html">Python</a><br><a href="https://lwu1822.github.io/fastpages/jupyter/2022/08/21/jupyter-notebook-1.html">Jupyter Notebook</a></td>
        {% endif %}

        {% if i == 1 %}
            <td> <a href="https://lwu1822.github.io/fastpages/bash/2022/08/26/tools.html">Bash: Check if tools are installed</a> <br> <a href="https://lwu1822.github.io/fastpages/code.org/2022/08/28/code-org.html">Learnings from code.org</a> <br> <a href="https://lwu1822.github.io/fastpages/java/2022/08/28/primitives.html">Java Primitives</a></td>
        {% endif %}

        
        {% if i == 2 %}
            <td><a href="https://lwu1822.github.io/fastpages/java/2022/09/05/w2-menu.html">Console Menu</a></td>
        {% endif %}

        {% if i == 3 %}
            <td><a href="https://lwu1822.github.io/fastpages/java/2022/09/07/w3-if-else.html">Iteration Minilab</a><br><a href="https://lwu1822.github.io/fastpages/misc/2022/09/09/w3-video.html">Focus/Habits</a></td>
        {% endif %}

    </tr>
    {% endfor %}
    


</table>
