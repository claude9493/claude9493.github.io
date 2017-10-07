# Sublime's Sao Operation - Snippet

  
## Background

Recently, I'm writing lots of codes, which shares a similarly structure. Like this:
   
	#include <stdio.h>
    int main(int argc, char const *argv[]){
    // Your Code
    return 0;
    }

Writing it again and again sometimes interputs my thinking.


## Sao Operation

### Introduction
Many editors have auto-fill function, so does Sublime.

But using Sublime Text, users can develop their own auto-fill pattern.

Maybe you have heard Emmet, an useful and powerful plugin for front-end develoment, which has many useful auto-fill models for HTML and CSS.
But it's not convinent for other language like C, Java and Python.

In Sublime, there is an useful tool called Snippet. You can taste it by typing "lorem" without quotes in sublime and type tab.

  	Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
  	tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
  	quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
  	consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
  	cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
  	proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

A confused paragraph appears. It's an built-in Snippet.

To develop your own Snippet, Find `*new snippet*` in `Tools -> Developer`.

### Highlight
There is a template in the new tab:
  <snippet>
  <content><![CDATA[
    Hello, ${1:this} is a ${2:snippet}.
    ]]></content>
      <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
      <!-- <tabTrigger>hello</tabTrigger> -->
      <!-- Optional: Set a scope to limit where the snippet will trigger -->
      <!-- <scope>source.python</scope> -->
  </snippet>

The third line is the content in the Snippet. ${1:this} and ${2:snippet} are chooseble segments of content, i.e. when you input the tabTrigger (which discussed later) and type `tab`, not only the content appears but your **cusor is also already located at `${1:something}` and selected `something` which can be empty**.

Now tabTrigger, `lorem` in the last section is a tabTrigger. I think now you understand what's a tabTrigger.

Now scope, scope is the environment set in advance where this snippet works. The format is `source.scope1.scope2.scope3....`. You had better not modify the `source` in the head. `scopeN` can be c, python, md, etc. Also, it's admitted to not write `.scope`, that means the snippet works in all enviornments.

Important: Save your snippet in the default path and the filename extension should be `.sublime-snippet`

### Example
Here is two of my snippets.


    <snippet>
      <content><![CDATA[
    //=========================${1:ADD YOUR COMMENT}=========================
    ]]></content>
      <tabTrigger>sep</tabTrigger>
      <scope>source.c</scope>

    </snippet>


    <snippet>
      <content><![CDATA[
    #include<stdio.h>
    int main(int argc, char const *argv[]){
      ${1}
      return 0;
    }
    ]]></content>
      <tabTrigger>CC</tabTrigger>
      <scope>source.c</scope>
    </snippet>

You can think why I write them.


## Conclusion and Review
Sorry for no figure. Because I am lazy.

I advise you to use some short and easy to remember tabTrigger s.

Happy national holidays. I have been to `Guangzhou` this holiday.
