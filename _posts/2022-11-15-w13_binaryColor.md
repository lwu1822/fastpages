---
title: Binary Color
layout: default
description: A Binary Math illustrative application using HTML, Liquid, and JavaScript.
permalink: /frontend/binary
categories: [3.B, 3.C, C4.4]
tags: [html, liquid, javascript]
week: 13
type: pbl
---

<!-- Hack 1: add a character display to text when 8 bits, determine if printable or not printable -->
<!-- Hack 2: change to 24 bits and add a color code and display color when 24 bits, think about display on this one -->
<!-- Hack 3: do your own thing -->


{% assign BITS = 8 %}



<div class="container bg-primary">
    <header class="pb-3 mb-4 border-bottom border-primary text-dark">
        <span class="fs-4">Binary Math with Conversions</span>
    </header>
    <div class="row justify-content-md-center">
        <div class="col-8">
        {% for j in (0..2) %}
            <table class="table">
            <tr id="table">
                <th>Plus</th>
                <th>Binary</th>
                <th>Octal</th>
                <th>Hexadecimal</th>
                <th>Decimal</th>
                <th>Minus</th>
            </tr>
            <tr>
                <!-- 1st table: button that says "+1" -->
                <!-- onclick="add(1)", if change 1 to another number, can change increment -->
                <td><button type="button" id="add1{{ j }}" onclick="add(1, {{ j }})">+1</button></td>
                <td id="binary{{ j }}">00000000</td>
                <td id="octal{{ j }}">0</td>
                <td id="hexadecimal{{ j }}">0</td>
                <td id="decimal{{ j }}">0</td>
                <td><button type="button" id="sub1{{ j }}" onclick="add(-1, {{ j }})">-1</button></td>
            </tr>
            </table>
        </div>
        <div class="col-12">
            {% comment %}Liquid for loop includes last number, thus the Minus{% endcomment %}
            <!-- bits = 7 -->
            {% assign bits = BITS | minus: 1 %}
            <!-- some whitespace for easier viewing--> 
            <!-- 2nd table -->
            <table class="table">
            <!-- Print out value for 2^# on table-->
            <tr>
                {% for i in (0..bits) %}
                <td><p id="binaryNote{{ i }}{{ j }}"></p></td>
                {% endfor %}
            </tr>
            <tr>
                {% comment %}Build many bits{% endcomment %}
                {% for i in (0..bits) %}
                <!-- bulb id = 0-7, post lightbulb off pic -->
                <td><img class="img-responsive py-3" id="bulb{{ i }}{{ j }}" src="{{site.baseurl}}/images/w13Binary-bulbOff.png" alt="" width="40" height="Auto">
                    <!-- what does javascript:toggleBit mean? -->
                    <!-- button for "Turn on" -->
                    <button type="button" id="butt{{ i }}{{ j }}" onclick="javascript:toggleBit({{ i }}, {{ j }})">Turn on</button>
                </td>
                {% endfor %}
            </tr>
            <tr>
                <!-- 2nd table w/ light bulb -->
                {% comment %}Value of bit{% endcomment %}
                {% for i in (0..bits) %}
                <!-- Controls the box that h 0/1 when turn on/off-->
                <!-- value = "0": For "text" attributes, define the default value in the input box -->
                <!-- First box on the left = 0 -->
                <td><input type='text' id="digit{{ i }}{{ j }}" value="0" size="1" readonly></td>
                {% endfor %}
            </tr>
            </table>
        {% endfor %}
        </div>
    </div>
<div style="width:500px;height:100px;solid #000;" id="color"></div>

</div>




<script>


    const BITS = {{ BITS }};
    const MAX = 2 ** BITS - 1;
    const MSG_ON = "Turn on";
    const IMAGE_ON = "{{site.baseurl}}/images/w13Binary-bulbOn.gif";
    const MSG_OFF = "Turn off";
    const IMAGE_OFF = "{{site.baseurl}}/images/w13Binary-bulbOff.png"

    // IMPORTANT: print out value for 2^# in <p> tag
    for (let j = 0; j < 3; j++) {
        for (let i = 0; i < BITS; i++) {
            const binNote = document.getElementById('binaryNote' + i + j);
            binNote.innerHTML = (2**(BITS - 1 - i));
        }
    }

    
    

    // return string with current value of each bit
    function getBits(j) {
        let bits = "";
        for(let i = 0; i < BITS; i++) {
            // IMPORTANT: digit = last box w/ "0"
            // JS does auto type conversion
            // return in binary string
            bits = bits + document.getElementById('digit' + i + j).value;
        }
        return bits;
    }
    // setter for DOM values
    function setConversions(binary, j) {
        document.getElementById('binary' + j).innerHTML = binary;
        // Octal conversion
        // IMPORTANT: parseInt: Change binary string to base 10
        // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString
        // toString: if number in front, c use radix (base 8 in this case)
        // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toString
        document.getElementById('octal' + j).innerHTML = parseInt(binary, 2).toString(8);
        // Hexadecimal conversion
        document.getElementById('hexadecimal' + j).innerHTML = parseInt(binary, 2).toString(16);
        // Decimal conversion
        document.getElementById('decimal' + j).innerHTML = parseInt(binary, 2).toString();

        const test = document.getElementById('decimal' + 0).innerHTML; 
        const test1 = document.getElementById('decimal' + 1).innerHTML;
        const test2 = document.getElementById('decimal' + 2).innerHTML;
        document.getElementById("color").style.backgroundColor = 'rgb(' + test + ',' + test1 + ',' + test2 + ')';
         
        
    }
    //
    function decimal_2_base(decimal, base) {
        let conversion = "";
        // loop to convert to base
        do {
        let digit = decimal % base;
        conversion = "" + digit + conversion; // what does this do?
        // IMPORTANT: same as Math.floor() (but faster), returns largest integer <= provided #
        decimal = ~~(decimal / base);         // what does this do?
        } while (decimal > 0);                  // why while at the end? what is ~~?
        // loop to pad with zeros
        if (base === 2) {                        // only pad for binary conversions
        for (let i = 0; conversion.length < BITS; i++) {
            conversion = "0" + conversion;
        }
        }
        return conversion;
    }

    // toggle selected bit and recalculate
    function toggleBit(i, j) {
        //alert("Digit action: " + i );

        // IMPORTANT: Get the ID of each below (ID syntax like: ex: img#bulb.img-responsive.py-3
        // or p#test)
        // This ID refers to a specific element that matches the ID
        // https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById
        const dig = document.getElementById('digit' + i + j);
        const image = document.getElementById('bulb' + i + j);
        const butt = document.getElementById('butt' + i + j);

        // Change digit and visual

        // IMPORTANT: Change to off when bulb on
        if (image.src.match(IMAGE_ON)) {
            // IMPORTANT: change value of last box (w/ 0) to 0
            dig.value = 0;
            image.src = IMAGE_OFF;
            butt.innerHTML = MSG_ON;
        } else {
            // IMPORTANT: change value of last box (w/ 0) to 1
            // Change to on when bulb off
            dig.value = 1;
            image.src = IMAGE_ON;
            butt.innerHTML = MSG_OFF;
        }
        // Binary numbers
        const binary = getBits(j);
        setConversions(binary, j);
    }
    // add is positive integer, subtract is negative integer
    function add(n, j) {
        let binary = getBits(j);
        // convert to decimal and do math
        let decimal = parseInt(binary, 2);
        if (n > 0) {  // PLUS
        // IMPORTANT: MAX === decimal? if true, decimal = 0, if false, decimal += n
        // c also do:  decimal = MAX === decimal ? decimal = 0 : decimal += n;
        // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator#:~:text=The%20conditional%20(ternary)%20operator%20is,if%20the%20condition%20is%20falsy.
        decimal = MAX === decimal ? 0 : decimal += n; // OVERFLOW or PLUS
        } else  {     // MINUS
        decimal = 0 === decimal ? MAX : decimal += n; // OVERFLOW or MINUS
        }
        // convert the result back to binary
        binary = decimal_2_base(decimal, 2);
        // update conversions
        setConversions(binary, j);
        // update bits
        for (let i = 0; i < binary.length; i++) {
        // IMPORTANT: substr(strat index, end index), inclusive, EXCEPT WHEN start index = 0, then end at end index - 1
            let digit = binary.substr(i, 1);
            document.getElementById('digit' + i + j).value = digit;
            if (digit === "1") {
                document.getElementById('bulb' + i + j).src = IMAGE_ON;
                document.getElementById('butt' + i + j).innerHTML = MSG_OFF;
            } else {
                document.getElementById('bulb' + i + j).src = IMAGE_OFF;
                document.getElementById('butt' + i + j).innerHTML = MSG_ON;
            }
        }
    }

    
</script>

{% raw %}

<h2>Learnings from code:</h2>
<p>When I first looked at the code for the binary table, I was confused with some of the syntax. Below is a documentation of things that I learned and an explanation of the code.</p>
<p> Many buttons have an <code>id</code>. This id is later used in Javascript. Furthermore, this: <code> {{ i }} </code> is liquid syntax. The <code>i</code> is referred from the for loop, whose syntax is this: <code> {% for i in (<em>start-num</em> .. <em>end-num</em>)</code>. </p>
<p> Looking at the first button, there is a function called <code>add</code>. This results in calling the <code>add</code> function in JavaScript. Within the function, the <code>getBits</code> function is called and stored within the variable <code>binary</code>. This function takes the current values of the binary (the 0s or 1s underneath the light bulbs) and stores it into a variable called <code>bits</code>. Next, the variable <code>decimal</code> takes <code>binary</code> and converts it from base 2 into decimal. </p>
<p> The next part is confusing. Within the if statement, <code>n > 0</code> means that the +1 button was pressed, while the else statement means that the -1 button was pressed. The decimal of the binary value is then set to a certain number. In <code>decimal = MAX === decimal ? 0 : decimal += n</code>, <code>MAX === decimal</code> is a boolean expression which says that if true, the first option before <code>:</code> will run, and if false, the second option will run. <code>MAX</code>, as defined in the constructor, is equal to 255. Therefore, the code is saying that if the decimal (remember that the decimal is equivalent to the value of the 0s and 1s underneath the light bulbs) number is equal to 255, then when you add 1, turn the decimal number into 0 (since the maximum is 8 bits, 2^8 = 256, binary starts from 0, so maximum number is 255). However, if the decimal number is not equal to <code>MAX</code>, just add 1 to decimal. Same thing in the else part of the loop, only this time, it refers to if the -1 button is clicked. If decimal is 0, when the -1 button is clicked, go back to 255, otherwise, just decrease by 1. </p>
<p>After that, the decimal number is converted to binary and stored in the <code>binary</code> variable. To convert to binary, the <code>decimal_2_base</code> function is ran. Within the function, something new that I saw was the <mark>do while loop</mark>. I learned that the difference between this loop and the while loop was that the while loop would run only if the condition is fulfilled. The do while loop will always run once, and then if the condition in the <code>while</code> portion is fulfilled, the loop will run again. Within the loop, the variable <code>digit</code> is assigned to be equal to the remainder of the decimal number and the base, which when passed into the <code>decimal_2_base</code> function, was 2. <code>digit</code> is then passed into the variable <code>conversion</code> as a string. The next piece of code that I was confused about was <code>~~(decimal / base);</code>. This is the same as <code>Math.floor()</code>, but runs faster. This piece of code devices the two variables <code>decimal</code> and <code>base</code>, and rounds to the largest integer that is less than or equal to the value. </p>
<p>For example, if <code>decimal</code> = 5, and <code>base</code> = 2, <code>~~(decimal / base) </code> = <code>~~(2.5)</code> which will round down to 2. 

{% endraw %}