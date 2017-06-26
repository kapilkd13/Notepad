---
layout: post
title: "Travis, Appveyor and their Custom Badges"
description: Why this Blog!
headline: hello everyone
modified: 2017-05-22
category: Code-Testing
tags: [Travis Appveyor Badges]
imagefeature: cover1.jpg
comments: true
mathjax: 
---

Have your repository passed Travis(unix) and Appveyor(windows) tests. Well then you have earned your badge, so why not show it to the world. But official badges aren't much fun, right? Let's create some custom badges.

**The Official Way**

***On Travis***
On travis go to your repository link, It will be something like `https://travis-ci.org/<org-name or username>/<repo-name>`. Click on the build image and you will get a popup. Here select the format type( like md or rst) and you will get the code that you can embed in your README file.

***On Appveyor***
Go to your repo's link on Appveyor which will be something like `https://ci.appveyor.com/project/<org-name or username>/<repo-name`. Now go to settings tab and choose badges options from left side panel. Here you will see code to be embedded in your README(or any other) file for this badge to work.

***What about some other formats for which this embed code is not available***
For such cases you have [pandoc](https://pandoc.org/try/). You can use this online tool to convert one format to another, assuming that it support your desired format.

***But can we have custom badges with modified text from officials***
***travis says***: Naah. We don't want that. I mean its not very hard to figure out which one is Appveyor's build badge and which one is ours.
![Image of appveyor and travis build badge](../images/appveyor-travis.png)
***Appveyor says***: We does allow custom text for all the different scenarios like
* pendingText 
* failingText
* passingText
Here is an example `https://ci.appveyor.com/api/projects/status/32r7s2skrgm9ubva?svg=true&passingText=master%20-%20OK&failingText=master%20-%20Fails`