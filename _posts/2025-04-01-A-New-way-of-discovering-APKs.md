---
title: "A new way of discovering APKs"
author: 
  name: cybershaykh
  link: https://twitter.com/cybershaykh
date: 2025-04-01
description: "Mobile Security"
tags: [Mobile Security] 
---


# A New way of Discovering APKs

![APKs](assets/img/apk.jpg)

Have you ever wanted to conduct a test (static analysis) on a mobile application but can't seem to find the apk file online? Well , this happened to me today. I hopped on a new web3 program and wanted to check out their mobile application because it was in scope. I normally decompile the apk files of applications using https://decompiler.com then go through the files and code, I don't really perform dynamic analysis by proxying requests to burp yet  (Send me RAM (: )

I looked through every nook and cranny of the internet for the apk of this application and  couldn't find it, not even reddit could help me . I kept hopping from apk sites to blogs and even chrome extensions but to no avail. Turns out the answer to my problem was in the response of gemini AI to the google search (how to get apk from google play) I made which I overlooked for some time. After searching and searching, I went through the suggestions gemini AI made again and decided to try out the last suggestion which was apparently so simple - so simple but no blog post I read mentioned this method. 

This method works by using the [files by google](https://play.google.com/store/search?q=files%20by%20google&c=apps) application on your mobile device:

## Step by Step Approach

1. You need to first download the target application on your mobile device
2. Now Proceed to installing [files by google](https://play.google.com/store/search?q=files%20by%20google&c=apps) from the playstore
3. Open the files by google app , it should look like this:

![img 1](assets/img/img1.jpg)

4. Navigate to the Apps category where you'd see your installed applications. 

![img 2](assets/img/img2.jpg)

5. To get the apk of a desired Application, simply click on the three dots beside the app then click on 'share' .

![img 3](assets/img/img3.jpg)

That's all! You can now get the apk file of any app you want without any hassle and test away!
Most security researchers would give up and move on leaving all the attack surface and potential bugs to other researchers. Doing this gave me an edge on the program I'm currently on as I might have stumbled upon a critical issue simply by reading the source files of the application. Hopefully I'd be able to write about it if it's accepted. 

Well , until next time, stay safe and happy hacking (:

_cybershaykh_
