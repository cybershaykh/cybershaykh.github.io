---
title: "From Lack of email verification to Admin account, How I got access to the admin account of a gateway portal"
author: cybershaykh
  name: cybershaykh
  link: https://twitter.com/cybershaykh
date: 2025-06-17
description: "Security Research"
tags: [Application Security]
---

Recently, I was getting rusty and bored, then I  started looking for companies who had responsible disclosure programs to hack on and then I discovered this leading company that deals with HR tools and workforce management , a really huge company with lots of assets online, and from their acknowledgements page, I noticed it had not been visited by many security researchers making the chance of finding security issues quite high. 

I started my research and started hunting for vulnerabilities on this target and I was pumped with adrenaline seeing so many alive hosts it had after I did my initial reconnaissance, I'm more of a manual hacker and majorly use only subdomain enumeration tools along with httpx to filter out livehosts, from then on , most of what I do in terms of covering attack surface and testing is manual. Using [virustotal](https://virustotal.com) and [shodan](https://shodan.io) , I check for endpoints and other hosts that are active. 

The vulnerability I found has not been disclosed yet, so I'll refer to the site as target.com, after gathering live hosts, I visited some subdomains here and there that were built on salesforce and I searched for common security issues that might affect salesforce applications such as `not limiting guest user access` , `salesforce objects disclosure that might contain sensitive information` etc. I couldn't also create an account because it was community admins that were allowed to create accounts for external visitors or employees, although I discovered some endpoints that would have allowed external individuals create accounts, namely the `/site/selfRegister.apexp` endpoint but I got redirected from the page after some seconds (I should probably dig deeper into that later ). 

The main lead to the critical vulnerability occurred when I used shodan to discover live hosts , I used the search query `ssl:target.com http.html:login` which I picked up from an awesome security researcher, the results included live IP addresses that belonged to the target. I visited some that were built on Microsoft IIS and asp.net and tried bruteforcing `/aspx` endpoints on them but to no avail, I also noticed another subdomain was using the **__VIEWSTATE** parameter which is known to be vulnerable to [RCE through deserialization attacks](https://soroush.me/blog/2019/04/exploiting-deserialisation-in-asp-net-via-viewstate/), I tested it for that which took quite some deep research , I got a 500 internal server error when I tried my payload but my beacon never received the http pingback (I should go back to this also ;) , 

Finally, I moved on to the vulnerable IP address which eventually matched to the domain gateway.target.com, the portal lets users register themselves, creating credentials to request access to the target's products. I began assessing the app and noticed that it had a signup and login functionality, proceeding to sign up like any hacker would, I was hit with the road block `Only @target.com domains are allowed to signup!` , welps, what do I do now? Like any researcher, I started to think of ways I could bypass this access control check, my mind began racing and thinking about bypasses like email parser issues, searching for employee accounts on github, well none worked. 

This is where I finally witnessed what  having the hacker mindset and thinking outside the box many security researchers emphasized on felt like , while staring at the target on a rainy evening, my mind suddenly went *what would happen if you just input an email pretending to be an employee?* , right then I tried myemail@target.com and I was instantly led to creating a password, I created the password, proceeded to login and boom! I was in the gateway portal without any email verification. I was very surprised and with my heart racing , I couldn't believe I was able to enter the portal like that. 

I could see some requests and other employee email , I deemed it was a big of a issue enough for me to report and I went ahead to report instantly without trying to escalate and get the highest impact , which turned out to be a lesson for me. 

After reporting, I was replied by the triager with this reply ):


![target_1](assets/img/target_1.png)
 
 I was a bit discouraged after getting this reply because I deemed it a valid issue enough for it to be accepted but I wasn't going to give up. I revisited the application and started thinking of how I could escalate my privilege and earn the highest impact, I checked the sign up process again carefully this time and noticed a few things. 
 
 I proceeded to sign up for a new account ending with @target.com , and observed the requests while intercepting them with my burp proxy , I noticed that when creating a new account, a default role is added, something like:

```json
{"id":"","username":"<your-username>@target.com","employeeName":"","enabled":true,"changeOnFirstLogin":false,"roles":["IC_REQUESTER"],"password":"<your-password>"}
```

the default role of an employee is ["IC_REQUESTER"] , immediately , I remembered seeing some roles in another endpoint, namely "ADMIN AND REQUESTER",  while creating this new account, I modified this POST Request to create an account and added the "ADMIN AND REQUESTER" role: 

```json
{"id":"","username":"<your-username>@target.com","employeeName":"","enabled":true,"changeOnFirstLogin":false,"roles":["ADMIN AND REQUESTER","IC_REQUESTER"],"password":"<your-password>"}
```

I proceeded to login and then another BOOM! , I had admin access to the whole gateway portal and was able to see more than 500+ internal employee emails, access the requests they made, delete them and even create new ones.  It could also allow me delete and modify any employee's account. This would have been chaotic if discovered by a malicious actor as they could perform actions that would cost the enterprise. 

After discovering this, I created a new report and submitted the issue explaining the whole process and impact and I was replied with a better response appreciating me reporting the issue (:

![target_2](assets/img/target_2.png)

This vulnerability taught me a lot as an a security researcher and how to approach targets, It made me understand the intricacies surrounding being s person who hunts for security issues accross appliacations such as questioning everyhing, understanding how system works , and never assuming something is safe just because it appears so. 

It also made me realise that companies value impact and issues that would affect their business operations, so reporting issues that really affect and impact their core business operations is  very important. I guess this is the end of my story about this vulnerability, I hope to share more abou my journey and findings in security research while researching and learning much more. stay safe and happy hacking!

*~ cybershaykh*  ;)
