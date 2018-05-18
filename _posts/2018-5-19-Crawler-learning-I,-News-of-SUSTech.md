---
layout: post
title: Crawler learning I, News of SUSTech
excerpt_separator:  <!--more-->
---
### Background

Recently, I learnt basic python crawler technique(urllib, bs4, requests...). And I practiced what I learned by a small and interesting project, that is, getting all titles of [SUSTech news](http://sustc.edu.cn/news_events_/). In this case, I used jupyter notebook to write and run my codes.
<!--more-->
The two packages are used in this case.

	import urllib
	import bs4

### News
In the case, I only considered the Chinese news of SUSTech. But the idea and codes are similar when turn to Enghish news.

First, let's make clear where are the news titles. They are in the pages http://sustc.edu.cn/news_events_/p/*, the star sign represents the page number. Till now, there are totally 178 pages of Chinese news, which are from 2013 to 2018.
		
	base_url = 'http://sustc.edu.cn/news_events_/p/'
	titles = []
		
We will use a loop to visit all pages. `base_url` stores the same part of the urls we will crawler. And the titles we get will be added to `titles` iteratively.

### A Simple Demo
First, Let's try to get all contents of a page.

	url = base_url+str(1) 
    content = urllib.request.urlopen(url).read().decode('utf-8')

In this sentence, we used the `urlopen` method from `urllib.request` to send a request to the first page of news. By `urllib.request.urlopen(url)` we got an `http.client.HTTPResponse` object. And we can use the `getcode()` method to see the status code of this request. The result is

![](http://ovlm69ca3.bkt.clouddn.com/urllib....getcode%28%29)

Then we use the `read()` method the get all contents of this page. Notice that it's a Chinese page, so we need to decode it according to `utf-8` format. Its result is:

![](http://ovlm69ca3.bkt.clouddn.com/urllib...read.decode) 

Till now, the code for downloading the webpage is okay. Following, we create a BeautifulSoup object, namely `soup`,  basing on the content we got just now and use it to parse the pages.

	soup = bs4.BeautifulSoup(content)
    temp = [x.a.get_text() for x in soup.find_all('div', class_ = 'tit')]
    tit = [t for t in temp if len(t) > 4]

First line creates the parser. We used the `find_all` method to searching the news title. We used two parms 'div' and class_='tit'. First one is the tag where the titles are located. Latter is a keyword which ensure the tags found shoud have an attribute class and its value is 'tit', here we write class_ insted of class directyl because class is a pyton keyword. `soup.find_all('div', class_='tit')` return the following result:

![](http://ovlm69ca3.bkt.clouddn.com/sp180519_012514.png)

Now we don't ge the titles yet. The title texts are in an `<a> </a>` tag. So we use `x.a.get_text()` to get the text. `.a` selects the subtag. `.get_text()` returns the text enclosed by that tag. Here we used a list comprehension to traverse the results and get the title texts.

Those tags in Navigation Bar also satisfies our condition. Noticed that their length is exactly 4. So we use this feature to remoe them from the list `temp` by another list comprhension. Here is the result.

![](http://ovlm69ca3.bkt.clouddn.com/sp180519_013511.png)
 

### Write a function

Till now, all problems seem solved. So we can transform this demo to a function which can be called anywhere.

	def get_title(page = 1):
    base_url = 'http://sustc.edu.cn/news_events_/p/'
    if page <= 0:
        return 0
    else:
        url = base_url+str(page)
    if urllib.request.urlopen(url).getcode() != 200:
        return 0
    else:
        content = urllib.request.urlopen(url).read().decode('utf-8')
        soup = bs4.BeautifulSoup(content, "lxml")
        temp = [x.a.get_text() for x in soup.find_all('div', class_ = 'tit')]
        tit = [t for t in temp if len(t) > 4]
        return tit

It receive a page number and return the title text in that page as a list. We do not talk too much about it because all sentences are eplained in previous section.

### All news of SUSTech
It's easy to write a loop to get all news title from SUSTech official website using the codes above. Here is the result. Totally 1593 news are got.

![](http://ovlm69ca3.bkt.clouddn.com/sp180519_014238.png)

### What's more

#### How I know where the titles are in the page?
I usually use the Chrome Developer Tool to view the source code of a page. It also provides a tool to locate the selected element. 

![](http://ovlm69ca3.bkt.clouddn.com/sp180519_011215.png)

You can learn more about the `Developer Tool` from [HERE](https://developers.google.com/web/tools/chrome-devtools/?utm_source=dcc&utm_medium=redirect&utm_campaign=2018Q2).

#### What can we do with these news?

I take the course "Intro to Big Data" this semester. And its midterm project is about NLP(natural language processing. We can vectorize these news and analyse the with some machine learning algorithms. And show the interesting results by visualization method.

	import pandas as pd
	import jieba
	import sklearn

There are so many things we can do with these title texts.

#### My English is so poor...

Finishing this article, I feel my English is SO POOR...

![](http://ovlm69ca3.bkt.clouddn.com/%E5%9C%A8%E5%8D%97%E7%A7%91%E5%A4%A7%E5%AD%A6%E4%B9%A0%E5%BE%88%E8%BD%BB%E6%9D%BE%E7%9A%84)
