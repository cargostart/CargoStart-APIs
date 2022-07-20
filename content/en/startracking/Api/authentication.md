---
categories: ["API"]
tags: ["api", "authentication"] 
title: "Authentication"
linkTitle: "Authentication"
date: 2022-07-19
type: docs
weight: 10
description: >
  All our API calls require in their header an authentication token, a [JWT token](https://jwt.io/introduction).
---
This token is generated calling our **login** endpoint. 

> If you haven't done yet, please take a moment to watch our video **[CargoStart API a Sneak Peek introduction](/startracking/getting-started/#a-sneak-peek-introduction)** that quickly shows three distinct ways on how consuming our API.

## The Authentication

First, you need a user id and a password to log in; usually, these credentials are provided by your customer.

Now you can access our [login](https://api.startracking.aero/user/login) endpoint and retrieve your authorization token

```http
POST /user/login HTTP/1.1
Host: api.startracking.aero
Content-Type: application/json

{
  "UserName": "MyUserNamer",
  "Password": "MySecretPassword"
}
```

With the right credentials, you will obtain an **HTTP STATUS CODE 200** and a **JWT token** in the request body; otherwise a **401 error code** meaning you are Unauthorized.

## The Authorization
It is possible to extract valuable information from our token, in the PAYLOAD section such as the expiration date, usually set to **120 minutes**; this could help you to develop a system to refresh your token before the expiration.

## Things to Remember:

* One credential, one FreighForwarder (and its relatives' branches)
* After FIVE wrong login attempts, for security reasons, the account is blocked, and you have to contact our support team.
* The standard maximum number of requests are:
    - per second: 3
    - per minute: 20
    - per hour: 200
    - per day: 1500
    - per week: 3000

If you exceed these constraints, our API will return an **HTTP STATUS CODE 429**, too many requests.