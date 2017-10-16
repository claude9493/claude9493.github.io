---
layout: post
title: fflush(stdin);
excerpt_separator:  <!--more-->
---
# `fflush(stdin);`
	**Segmentation Fault** in my C HW has puzzled me for a long time. 
	Today, I managed to solve the problem and almost finish my HW.
<!--more-->
### Part I. My C HW
This semester, I took the course CS205 C/C++. Its Lab2 asked us to make a program which can calclute distance between arbitary two cities from provided data file.
You can download the description file 
[here](http://ovlm69ca3.bkt.clouddn.com/LAB2.pdf "Here").

----------

### Part II. My BUG
The loading data process is simple which is finished first. As well as the search part. 

However, meeting the **re-input** (i.e. the second input), my program crashes because of the `segmentation fault`. It do puzzled me lot of days.

In today's lab, I asked my teacher for help, he told me to add `fflush(stdin);` after each `scanf()`. It works, it rescue my program.

----------

### Part III. Principle
When I use scanf to read a city's name from the keyboard, I write like this: 
	
	scanf("%[^\n]", input);
It works well in the aspect of reading city whose name consists blank, like New York City, Hong Kong. 

But in the deep of computer, the ingored `\n` still exists in the **buffer**. So in the next time the program meets `scanf()` statement, the newline is readed first. Then whatever input is missed. Because it immedaitely go ahead and run following statements. 

I think it seems like a queue structure I learned in last DAAS class.

##### So what the does `fflush(stdin);` do?

Acatually, fflush() function clear the buffer.

Maybe You have met the situation that the `printf()` doesn't work in the order of code. It is because computer stores the output in the `Buffer` of **stdout** temporarily. And it will release it later (usually in the end of the program). So in this case, you can use `fflush(stdout)` to make the program do the print work immideately. In this case, fflush clear the stdout buffer, by put them out in the screen.


Similarly, in the aspect of input, there is a stdin buffer as well. All the input from the key board are stored in the buffer first, and are released when meeting scanf. So in my program, 

	scanf("%[^\n]", input);

This statement stops when meeting the newline char, but it is still read and stored in the stdin buffer, next time `scanf("%[^\n]", input);` is executed, the '\n' is read first, and it stops immideately, sothat the error appears.

In this case, fflush clear the stdin buffer, by make it empty again.

### Part IV. End
All the above explanations are not specific and professional. Those are just my understand.
 
for a more professional explanation, I recommend you to search it on wiki or books, and I believe you will understand it better.

Here is a running time screenshot of my program. 

![](http://ovlm69ca3.bkt.clouddn.com/distance.png)