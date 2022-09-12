---
layout: page
title: Weekly Work
permalink: /weekly-work/
---

## Week 0

* [First post](https://lwu1822.github.io/fastpages/markdown/2022/08/19/post-1.html)

* [Java](https://lwu1822.github.io/fastpages/2022/08/20/java.html)

* [Python](https://lwu1822.github.io/fastpages/2022/08/20/python.html)

* [Jupyter Notebook](https://lwu1822.github.io/fastpages/jupyter/2022/08/21/jupyter-notebook-1.html)

## Week 1

* [Bash: Check if tools are installed](https://lwu1822.github.io/fastpages/bash/2022/08/26/tools.html)

* [Learnings from code.org](https://lwu1822.github.io/fastpages/code.org/2022/08/28/code-org.html)

* [Java Primitives](https://lwu1822.github.io/fastpages/java/2022/08/28/primitives.html)



<table>
    <tr>
        <th>Week</th>
        <th>Assignments</th>
    </tr>
    
    
    {% for i in (0..2) %}
    <tr>
        <td>{{ i }}</td>
        {% if i == 0 %}
            <td><a href="https://lwu1822.github.io/fastpages/markdown/2022/08/19/post-1.html">First post</a> <br> <a href="https://lwu1822.github.io/fastpages/2022/08/20/java.html">Java</a> <br> <a href="https://lwu1822.github.io/fastpages/2022/08/20/python.html">Python</a><br><a href="https://lwu1822.github.io/fastpages/jupyter/2022/08/21/jupyter-notebook-1.html">Jupyter Notebook</a></td>
        {% endif %}

        {% if i == 1 %}
            <td> <a href="https://lwu1822.github.io/CSP-fastpages/python/2022/09/05/w1-python-quiz.html">Python quiz</a> <br> <a href="https://lwu1822.github.io/CSP-fastpages/bash/2022/09/05/tools.html">Bash: Check if tools are installed</a> <br> <a href="https://lwu1822.github.io/CSP-fastpages/notes/">Notes</a></td>
        {% endif %}

        
        {% if i == 2 %}
            <td><a href="https://lwu1822.github.io/CSP-fastpages/python/2022/09/05/w2-dictionary.html">Dictionary</a> <br> <a href="https://lwu1822.github.io/CSP-fastpages/html/2022/09/05/2_html-css.html">HTML and CSS</a></td>
        {% endif %}

    </tr>
    {% endfor %}
    


</table>
