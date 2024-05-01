---
title: "A Primer On Social Engineering"
author:
  name: cybershaykh
  link: https://twitter.com/cybershaykh
date: 2024-04-25
description: "Talking about social engineering"
tags: [Human Hacking]
---

![social engineering](assets/img/social_engineering.jpg)

Have you ever heard of the term social engineering? you might think of it as a way of improving the society? Well no, social engineering is not that at all, it is commonly known as “human hacking”. In [cybersecurity](https://www.cisco.com/c/en/us/products/security/what-is-cybersecurity.html#:~:text=Cybersecurity%20is%20the%20practice%20of,or%20interrupting%20normal%20business%20processes.), we always hear of attackers crafting the most dangerous payloads, launching [denial of service](https://www.cloudflare.com/learning/ddos/glossary/denial-of-service/) attacks against billion dollar companies and stories of teenagers sitting in front of their computer screens all day with their black hoodies trying to steal money or intellectual property by circumventing the normal mode of operation of a computer system — a term known as [hacking](https://www.fortinet.com/resources/cyberglossary/what-is-hacking#:~:text=Hacking%20in%20cyber%20security%20refers,or%20disrupt%20data%2Drelated%20activity.) . Well, I’m here to tell you that there is a human element to every cyber attack. Social engineering as defined by [Christopher J. Hadnagy](https://en.wikipedia.org/wiki/Christopher_J._Hadnagy) is “any act that influences a person to take an action that may or may not be in his or her best interests.” It is a way of influencing people either by manipulating or convincing them into making a decision that may or may not be of harm to them. In this article, I’ll be touching on different types of social engineering attacks, how you can identify them and ways you can protect yourself against them. Many people encounter these scenarios I’m about to share but most don’t pay attention to them because we humans are not perfect and there are loopholes in our mode of thinking which makes us susceptible to attacks, hence the famous quote _“ the human element is the weakest link in cybersecurity”._

## Types of Social Engineering attacks

On a daily basis, we encounter many different scenarios either offline or online, it could be meeting a new person on the internet, recieving a phone call from someone asking for information or engaging in a social media trend that asks you to post something about your personal life. Some of these scenarios might actually be an attack on you, but it seems harmless since you feel in control all the way. Here are some examples of some common social engineering attacks:

![examples of social engineering attacks](assets/img/examples_of_social_engineering_attacks.jpg)

At number 1, we have the big bad wolf which I’m sure everyone has heard of :

- Phishing : It is described as an attempt to steal sensitive information, typically in the form of usernames, passwords,credit card numbers, bank account information or other important data in order to utilize or sell the stolen information. Attackers “fish” for people’s personal information all the time, they always want to have access to your online accounts, empty your life savings and perform all sort of nefarious acts.
  
Phishing is majorly carried out by sending malicious emails to hundreds of users and waiting for whoever falls for the trap, they pose as reputable organizations you use such as your banks, social media applications or other companies. Most of the time, people do not calmly read through their mails and carefully verify if it’s truly the legitimate organization that sent them an email asking them to reset their password, click a link to win a free gift or even download an attachment. All of which are set out to compromise the system of the user. You might wonder, since I’m just clicking a link, then where is the manipulation or as I like to say “human hacking” coming from? Well there is something in psychology known as the six principles of persuasion which are:

1. Reciprocity
2. Commitment and Consistency
3. Social Proof
4. Liking(Likability)
5. Authority
6. Scarcity (Urgency)

Human beings tend to get a rush of adrenaline (a hormone released by your body when you’re excited) when they get an email saying they’ve gotten a gift or have been accepted for the job they applied for. Sometimes, we are even distracted and are just non-chalant when going through our mails, this gives the attacker a chance to play on our minds and get us to click that link thereby giving them access to our personal infomation. Asking yourselves questions like could this be true? What company is sending me this mail? Is the [domain name](https://en.wikipedia.org/wiki/Domain_name) spelt correctly? What if this is actually a scam? Would someone really give me money or a brand new phone for free? These questions decrease the chances of you falling for a phishing attempt. Take a look at this sample of a real email and a phishing email and see if you can spot the differences!

![phishing_email](assets/img/phishing_email.jpg)

They look so similar right? Attackers are so crafty and creative when creating these emails that it is almost impossible to tell a real email from a phishing email, with the rise of [Generative Artificial intelligence](https://www.techtarget.com/searchenterpriseai/definition/generative-AI) , it is now easier for scammers to create emails with no grammatical errors, and convincing statements making it easier for people to fall for them.

- Spear phishing is another form of phishing that targets a particular individual rather than spraying emails and hoping a fish catchs the bait. You can also call it specific phishing as a lot of information([OSINT](https://en.wikipedia.org/wiki/Open-source_intelligence)) is gathered on the target indivdual in order to craft a very personalised attack based on the interest of the individual.
  
- Whaling is when an attacker targets the leaders or people in high positions of a company. People like the CEO, CTO or Managing Directors of the organization, whaling can be a big move but would be effective since it gives access to sensitive information immeadietly and the attacker might not need to start going through a maze if he/she had phished a lower level employee.

Phishing comes in different forms, it is not only through an email address your personal information can be stolen. There are other forms of phishing such as:

- Vishing : Vishing is short for voice phishing, it is a type of attack where an attacker tries to get personal information by impersonating any individual (also known as pretexting) over the phone or by talking to them in person. Most of us would have recieved a call from an worker claiming to be with our bank and asking us for private information like our BVN(Bank Verification Number), this is where pretexting comes in, attackers try to impersonate individuals and act as if they are in a position of authority to extract information from people. Many people have contacted me, telling me their Whatsapp got hacked and this happened by them giving out their security code over the phone to a person who cooked up a fake but enticing story to get their code. This is a popular form of vishing attack.
  
It has even gotten very advanced with the rise of Artificial Intelligence, voices of your loved one’s can now be cloned, making it seem as if they are the one requesting something from you as shown in this twitter [post:](https://x.com/RachelTobac/status/1660432071003881474?s=20)

Social engineering is getting very advanced and new methods allow people to fall prey easily by playing on human psychology. The last form of phishing attack I’ll be talking about is SMS Phishing which is also known as smishing.

- Smishing, also known as SMS phishing is just another form of phishing attack but with text messages, remember those SMS messages you get telling you to come start a job and start earning a whole lot of money per day or the one asking you to come pick up a delivery you never ordered for!

  ![smishing](assets/img/VR_hiring.jpg)
  
The image above was an attempt to tempt me into contacting them to get a job which is most likely not true. No company willing to hire you would send you a text message with a phone number for you to contact them! A person who is desperately looking for a job would have thought it to be true and proceed to contact them. They would most likely try to scam that individual by making them pay a so called “ registration fee” or whatnot. These are ways by which attackers try to rewire and trick our minds into making bad decisions.

Phew, that was a long ride talking about phishing, well the ride is not over yet. Phishing is just one of the most common ways people get attacked. Let’s see other methods people might not be aware of.

The next on the list is :

- **Baiting: A type of social engineering attack where a scammer uses a false promise to lure a victim into a trap to steal personal and financial information or inflict a system with malware.**
  
This is a way by which scammers use tempting items or statements to manipulate people into divulging their personal information. You must have seen adverts like _“Congratulations, you have just recieved a brand new iPhone, click here to recieve it”_ this is an example of a baiting attack, attackers feed on human greed and curiosity to trick them into believing they could actually get a free gift, well be careful because when someone is claiming to give you something for free online, you’re most likely the product!

Another way attackers bait people is by using physical materials. Attackers sometimes go to business centres, banks, offices, public places, etc. then randomly throw USB drives filled with malware (also known as rubber duckies) on the walkway, at least one person would becurious enough to carry the infected USB drive, plug it into their office or home computer hoping that a movie or something interesting is on it. Well, they were wrong and have succesfully granted the attacker access to their entire office or home network. These are some ways by which people with malicious intent play on our psychology and get the most out of us.

Moving on, the next term I’ll be touching on is “_pretexting_”. Pretexting is mostly used to further or improve other social engineering attacks. It is when an individual poses to be who they are not in order to get access to privileged information as we have seen in phishing. An attacker that is using a pretext may pose as whomever will suit a particular scenario. For example if I want to get access to personal records of customers from a company, I may call the reception and pretend to be a manager to fool the receptionist into giving me access to sensitive information. Using a pretext involves studying who you are trying to impersonate and making sure the victim you are trying to attack dosen’t suspect you to be lying.

- Dumpster diving is one of the elements also used in improving the success of a social engineering attack although it involves some dirty work! From it’s name, it involves going through the dirt or trash of companies or individuals looking to find information which might be sensitive. People are non-chalant about what they throw in the trash that they sometimes put items like receipts, files with private information, papers they wrote their passwords(bad practice) or even USB files that contain their personal data in their dumpster. Dumpster diving is a proven way of getting first hand information that can be used in the course of an attack.
  
- We also have another form of social engineering known as tailgating. Picture this, you need access to a company but you don’t have an ID card or a means of identifying you as a legitimate entity of the company. But you found a way to sneak in by following a legitimate employee of the company by walking so close to them and the security guard skipped you. Another way of tailgating is by getting someone already allowed in the place you’re trying to access give you an item to hold, then you proceed to give them the object inside the company without being checked by the guards. They most likely thought since he’s holding a package for the person we already checked or since he’s tagging along with them, the chances he’s allowed to be here is high so let’s just leave him. There are so many ways anybody can tailgate, these are just some of the common methods.
  
Alright, we’ve come to the end of this article and I’ll be explaining the concept of _ransomware_ and _pig butchering_ and how they relate to social engineering in another article! Stay tuned for it…

Before rounding off, here are some tips you can apply both online and offline to decrease the chances of you falling for a social engineering attack :

- Verify! Verify!! Verify!!! : Always verify and confirm who you are talking to online most especially on voice calls and if the caller is requesting for personal information. Don’t blindly disclose your sensitive information with anyone!
  
- _can you read me the code you just recieved, click the link i just sent you, what is your … number, do you remember your password? All these statements and anyone in these formats are red flags_! Do not tell anyone pins, codes and passwords that can be used to authenticate you to some form of service even if they claim to be from your bank , social media company or anywhere…

 - Be calm and double check when reading your mails, check the sender’s email address, the domain name and the message in general for any inconsistencies and grammatical errors. Do not download attachments blindly from emails. Ensure any link you’re clicking is truly from a legitimate organization you use, virustotal.com is a website you can use to check the safeness of online links.
   
- Think before you leap, always ask yourself questions before you make any decison, sending any message or divulging personal information. Make sure what you’re about to do cannot harm you in any way…
  
- Be careful of what you put online — 99.9% of a social engineer’s work is gathering information
- Don’t trust blindly (because they sound nice doesn’t mean they won’t steal your money)
  
I hope I’ve been able to enlighten you about some methods by which social engineer’s carry out their attacks. Remember that :

![goal of social engineer](assets/img/goal_of_social_engineer.jpg)

So think twice before you make any decision and be sure to educate your friends and loved ones about the dangers of social engineering… Till next time, STAY SAFE!

_~cybershaykh_
