---
toc: true
layout: post
description: Recording my learnings on using Jekyll.
categories: [jekyll-liquid]
title: Jekyll and Liquid
---

<p style="font-size: 5px"><em>this took me hours to research btw</em></p>

While I was setting up my fastpages blog, I noticed this interesting line of code in `index.html`. 

![](https://lwu1822.github.io/images/index_html_code.png "code in index.html to insert image")

And I thought, *hey, this is interesting, what does {% raw %} {{site.baseurl}} {% endraw %} do?*

After some [googling](https://www.google.com/), I found that {% raw %} `{{site.baseurl}}` {% endraw %} wasn't something in Markdown. Turns out it's actually Jekyll syntax. 

So what does {% raw %} `{{site.baseurl}}` {% endraw %} do? 

Basically, `baseurl` is the directory under the URL of the website. [^1] So for example, this blog's URL is `lwu1822.github.io`, and the baseurl is `fastpages`. 

So I can just do {% raw %} `![]({{site.baseurl}}/images/diagram.png)`. {% endraw %} Saves a lot of typing.

Pretty cool, huh? 😊

<br>

**Something else I encountered while making this post** 

{% assign openTag = '{%' %}

To type {% raw %} `{{site.baseurl}}` {% endraw %} in this Markdown file, apparently you have to use the {% raw %} `{% raw %}` {% endraw %} and `{{ openTag }} endraw %}` template around {% raw %} {{site.baseurl}} {% endraw %}. [^2]

Like this:

```
{{ openTag }} raw %} {% raw %} {{site.baseurl}} {% endraw %} {{ openTag }} endraw %}
```

<br>

**Also something I encountered just as I was writing the line above**

Notice how I was able to write `{{ openTag }} endraw %}` above? Unfortunately, it's not that simple to just type it directly into your IDE, like this:

> :warning: **Warning**: Don't do this, it will break your code:


```
{{ openTag }} raw %} {{ openTag }} endraw %} {{ openTag }} endraw %} 
```

The reason is because the first {{ openTag }} endraw %} will be interpreted as ending the {{ openTag }} raw %} template. 

So if you want to be able to type `{{ openTag }} endraw %}` in Markdown, you need to do the following [^3]:

1. Create a variable, in this example, I'll name it `openTag`, and assign it to `{{ openTag }}`:

{% raw %}
    ```
    {% assign openTag = '{%' %}
    ```
{% endraw %}

2. Use the {% raw %} `{{ openTag }}` {% endraw %} variable anytime you want to type text that contains `{{ openTag }}` in it.

    For example, to type the text `{{ openTag }} endraw %}`, you would do:

{% raw %}
    ```
    {{ openTag }} endraw %}
    ```
{% endraw %}


<br>

**Even more something that I learned**

Apparently, you also can't type `{{ openTag }}` directly in the IDE, which would also break your code (took me a long time to debug （ꐦ𝅒_𝅒）)

Instead, you have to type: {% raw %} `{{ openTag }}` {% endraw %}

<br>

###### Things for me to contemplate on: 

I noticed on the provided [Fastpages Notebook Blog Post](https://lwu1822.github.io/fastpages/jupyter/2020/02/20/test.html), you can add an image without the baseurl. For example, you can specify an image with `![](images/diagram.png)`. Not sure why that works, but I'm guessing it has something to with Jupyter Notebooks.

<br>

[^1]: [baseurl](https://mademistakes.com/mastering-jekyll/site-url-baseurl/)

[^2]: [Liquid template language](https://shopify.github.io/liquid/tags/template/)

[^3]: [I took the steps from here but quite frankly, I found the explanation a little confusing, so I simplified it as much as I could in this blog](https://blog.slaks.net/2013-06-10/jekyll-endraw-in-code/)