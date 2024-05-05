---
title: "Introduction To API Hacking"
author: 
  name: cybershaykh
  link: https://twitter.com/cybershaykh
date: 2024-05-01
description: "Talking about social engineering"
tags: [API HACKING] 
---
 
 ![api hacking](assets/img/api_hacking.jpg)

Applications (Both WEB and MOBILE ) nowadays have to use a lot of resources in their operations, Application Programming Interface (API) are used to call on resources that an application needs to function well, they let different software components interact with each other to exchange information. They exchange resources such as data, features and other functionalities with some other backend logic or database. Think of it as a restaurant where you have multiple customers to serve, the chef is in the kitchen cooking and it would be impossible to serve customers whilst cooking right? This is where diners(our API’s) come in, they take the prepared food (data) from the kitchen, which is our backend or database to our hungry customers — our end users at the front end.

![api working](assets/img/api_working.jpg)

There are different types of API’s such as :

 - RESTful API’s
 - Graphql
 - SOAP , etc.
We also have :

1. Public API’s — API’s that can be used and accesssed by anyone
2. Partner API’s — Some companies share API’s with each other in order to share data and resources, they are known as Partner API’s
3. Private API’s — These are API’s that are to be used within an organization.
API’s generally have the structure : ``` https://api.example.com/v1/users ```

The /v1 means version 1, API’s can have different versions depending on thier usage. The /users part of the API is known as an endpoint. An API endpoint is a specific url which has a resource or data that can be accesseed simply by browsing to that url. The /users endpoint would typically return the users of that particular application. To learn more about API’s , visit this [link](https://www.ibm.com/topics/api)

API’s are interesting because they handle a lot of information and data, they allow applications use data and functionality from other apps instead of building them from scratch. Because API’s process a lot of data, vulnerabilties can surface in many different ways.

## What is API Hacking?

API security testing or hacking is a way of testing and ensuring that the API’s used in a certain application are secured from vulnerabilities that can make the API behave in an unintended way or make attackers get unauthorised access to data. API’s handle a lot of resources and are used heavily when building applications, deploying API’s without testing them leaves room for attackers to abuse functionality, gain access to unauthorised information, disrupt business processes thereby costing the affected application negatively. APIs are tested in accordance to the [OWASP (Open Web Application Security Project) API security top 10 list](https://owasp.org/API-Security/editions/2023/en/0x11-t10/). The OWASP API security top 10 gives a highlevel overview of the most dangerous vulnerabilities affecting API’s.

### Why Do API’s get Attacked?

- Access to sensitive data : API’s mostly have access to sensitive data, making them a goldmine for attackers
- Manipulation of functionalities : Functionalities can be abused to perform a harmful action, for example you have users on your application and an admin also, an API that was not properly written or tested could make an ordinary user escalate their privilege to an administrator — this is a common vulnerablility in API’s known as Broken Function level Authorization (BFLA)
 - Disruption of services: API’s can recieve too many requests more than which they can handle, often known as a denial of service attack which can make the API unavailable to those who are genuinely in need of it.
- Financial gain: API’s are also targeted for financial purposes, an API that wasn’t properly configured would be harmful in a bank application for instance.
  
### Examples of API Vulnerabilities.

1. Broken Object Level Authorization — BOLA
- Occurs when a user can see the information of other users
- Manipulating API objects to view items belonging to other users
2. Broken Authentication
- Weak or Poor authentication
- Weak password
3. Broken Object Propery Level Authorization
- Exploting endpoints by reading and/or modifying values of objects
- Revealing unneccessary sensitive data
4. Unrestricted Resource Consumption
- Abusing API calls due to high volumes of API calls, large requests
- Missing inadequate rate controls
5. Broken Function Level Authorization — BFLA
- Abuse of API endpoints to improperly modify objects
- Modify account roles
6. Unrestricted access to sensitive business flows
- Abuse of a legitimate business workflows through excessive , automated use
- Rate limiting , CAPTCHAs not always effective against fraudulent traffic
7. Server Side Request Forery
- Exploiting URL inputs to make a request to a malicious 3rd party server
- Can lead to data leaks
8. Security Misconfigurations
- Risks that can arise from misconfigurations
- Unneccesary features enabled
9. Improper Inventory Management
- Unauthorised APIs access via old unused APAPI versions
- Forgotten APIs
10. Unsafe Consumption of APIs
- Exposures and Exploitation through 3rd party APIs

### How to better Secure your API’s
- Limit the amount of data an api endpoint is revealing.
- Validate who is requesting access to an endpoint each time.
- Ensure the use of rate limiting — this is too protect your api from reciveing too many requests.
- Validate and Sanitize all user inputs to prevent injection vulnerabilities such as SSRF(Server Side Request Forgery)
- Implement access controls on the endpoints.
- Review your API configurations and test them.
- Ensure your API documentation is up to date.
- Perform proper asset management and ensure that forgotten API’s which are no longer is use are deleted.
These are just tips which can help you proper manage and secure your API’s, there are so many ways API’s can get attacked.

In the coming articles, we’ll be looking into each of the OWASP API Security top 10, what they are, where they can be found , real world scenarios of breaches by API’s and how you as a developer can protect against them. See you soon!

_~cybershaykh._
