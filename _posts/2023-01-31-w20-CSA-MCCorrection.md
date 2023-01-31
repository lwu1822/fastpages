
---
toc: true
layout: post
description: 
categories: [misc]
title: MC Corrections
comments: true
---

My score is 48/52.

The question that I got wrong was #9. I thought that `num = str.substring(0, 3).length()`. Turns out the actual length of num is the entire length of "CompSci", which is 7. 

Another question that I got wrong was #12. I learned that with `System.out.println`, even if the elements in the ArrayList was changed, `System.out.println` will print out the original elements, and then change it. Therefore, the first line is "Alex, Bob, Carl", rather than "Alex, Alex, and Alex" (after change). 

I also got #19 wrong. I picked that the method finds the index of the first occurrence of the string. However, since the for loop runs until the end of the string, the last occurrence of the string will be the output. 

I got #40 wrong because I selected II and III. However, II is wrong because if the ArrayList's elements are removed, some elements will be swapped. III works because the loop moves from right to left; therefore, if some elements are removed, the elements to the left of it are not affected.
