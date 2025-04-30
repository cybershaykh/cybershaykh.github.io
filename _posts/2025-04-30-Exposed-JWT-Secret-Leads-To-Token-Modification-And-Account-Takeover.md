---
title: "Exposed JWT Secret Leads To Token Modification And Account Takeover"
author: 
  name: cybershaykh
  link: https://twitter.com/cybershaykh
date: 2025-30-04
description: "Exposed JWT Secret in JWT Token"
tags: [Web Security] 
---

# 🔐 Exposing a Critical JWT Vulnerability: Secrets in the Payload?!

## Introduction

JSON Web Tokens (JWTs) are a common way for web applications to handle authentication. When implemented correctly, they are efficient and secure. But when done poorly, they can open the door to serious security breaches.

In this post, I’ll walk you through a  vulnerability I discovered during a routine session on a web platform , I'm not allowed to name the application so we'll  call it `example.com`. The flaw? The JWT secret key, the one responsible for verifying tokens was embedded directly in the JWT payload.

Yes, **the signing secret was being sent to the client inside the token itself**. Here's why that’s a major issue, how I verified it, and what developers must do to avoid this kind of mistake.
## A Quick JWT Refresher

JWTs are made up of three parts:

1. **Header** – indicates the signing algorithm and token type. e.g. HS256
2. **Payload** – contains the claims (user data).
3. **Signature** – ensures the token hasn't been tampered with.

`eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9 . eyJpZCI6InVzZXJfaWQiLCJlbWFpbCI6Im1lQGV4YW1wbGUuY29tIn0 . [Signature]`

These parts are base64-encoded and concatenated with dots. While encoding makes the content compact and URL-safe, it **does not** encrypt or hide anything—**anyone can decode a JWT and read its contents**.

### The Vulnerability: Secret in the JWT Payload 😱

After signing up on `example.com`, I captured the JWT sent to the client. Upon decoding it, I noticed something alarming in the payload:

``` json
{   "id": "cm4jpw0wa42uiw3mkmdvkvd9q",   "email": "me@example.com",   ...   "secret": "86qPY/sQX7CK2oU+MDfHPoYiAdVifK5W4ACUHnbsjbkulWfyd4yhaB4FLlVhaWA+",   "expiresIn": 86400,   "iat": 1733911151,   "exp": 1733997551 }
```

Yes, that `secret` field is **the actual key used to sign the JWT**.

### Why This Is a Big Deal

The JWT secret is supposed to be kept server-side only. By including it in the payload, `example.com` inadvertently gave every user the power to:

- Forge their own tokens
- Modify claims such as `email`, `role`, or `isAdmin`
- Impersonate other users or escalate privileges
- Completely bypass the authentication logic
## Demonstrating the Exploit

Here’s how I confirmed the vulnerability:

 # 1. Decode the Token

Using [jwt.io](https://jwt.io), I decoded the JWT to inspect the payload and retrieve the secret.

2. Craft a Forged Token
Using Node.js and the `jsonwebtoken` package, I generated a fake token:

``` javascript
const jwt = require('jsonwebtoken'); const secret = "86qPY/sQX7CK2oU+MDfHPoYiAdVifK5W4ACUHnbsjbkulWfyd4yhaB4FLlVhaWA+";  const payload = {   id: "cm4jpw0wa42uiw3mkmdvkvd9q",   email: "me@example.com",   isLender: true, // modified claim   iat: Math.floor(Date.now() / 1000),   exp: Math.floor(Date.now() / 1000) + 86400 };  const token = jwt.sign(payload, secret, { algorithm: 'HS256' }); console.log(`Forged JWT: ${token}`);
```

 3. Use the Forged Token

I sent the forged token in the `Authorization` header and successfully accessed features reserved for privileged users. the `isLender` field was false when I created an account was false , but when I forged the token, I was able to upgrade my privilege and make my self a Lender by setting the role to `isLender: true`

**Impact**: Complete account takeover and unauthorized access.
## How This Happened

The developers at `example.com` likely misunderstood the purpose of the `secret` field or tried to customize the token for internal logic without realizing the consequences.

This is a classic case of _security through obscurity_ gone wrong. Since JWTs aren’t encrypted, anyone can decode and extract that secret.

## How to Fix It

#### 1. **Never Include Secrets in the Payload**

The JWT payload is public. It should **never** contain passwords, API keys, tokens, or secrets.

#### 2. **Store Secrets Server-Side**

Keep the signing secret in a secure environment variable or secret manager—never expose it to the client.

#### 3. **Use Asymmetric Signing (RS256)**

Switch to RS256 where a private key signs the JWT and a public key is used for verification. That way, even if the public key leaks, the private key remains safe.

#### 4. **Validate Claims Server-Side**

Always double-check important claims (`role`, `isAdmin`, etc.) against your database rather than trusting what's in the JWT blindly.

#### 5. **Use Short Expiry Times**

The longer a token is valid, the longer an attacker can misuse it. Keep expiry times minimal and refresh tokens securely.

#### 6. **Regular Security Audits**

Run regular code reviews and penetration tests. Sometimes the biggest issues are hidden in plain sight.

## Conclusion

JWTs are powerful tools—but only when used properly. Including the signing secret in the payload is like taping your house key to your front door and hoping nobody looks.

This vulnerability at `example.com` illustrates how small mistakes in implementation can have **huge** consequences. If you’re building or maintaining an app that uses JWTs, take this as a reminder to **review your token logic immediately**.
