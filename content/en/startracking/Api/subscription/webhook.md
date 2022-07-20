---
categories: ["API"]
tags: ["api", "Webhook"] 
title: "Webhook"
linkTitle: "Webhook"
date: 2022-07-19
type: docs
weight: 30
description: >
  
---
> We assume you are already familiar with our API and authentication; if not please watch before:
> * **[CargoStart API a Sneak Peek introduction](/startracking/getting-started/#a-sneak-peek-introduction)**
> * **[StarTracking Authentication and Authorization](/startracking/api/authentication/)**

In short, when one of the desired events are triggered (such as Routemap replan, Milestone Update, etc.), StarTracking will send an HTTP POST payload to a sender webhook's sender URL.

All you need is to develop - using your preferred language - a brand new simple WebAPI Server or to implement a Notification endpoint in your WebAPI Server.

## Insert a Webhook
Inform StarTracking WebHook service the URL address and the endpoint where to notify all the notification payload.

```http
POST /ffw/startracking/routemap/webhook HTTP/1.1
Host: api.startracking.aero
Accept: application/json, text/plain, */*
Content-Type: application/json;charset=UTF-8
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczovL2FwaS5zdGFydHJhY2tpbmcuYWVybyIsInN1YiI6IkZWQUdPQ01QIiwibmJmIjoxNjU4MjQwMTgzLCJpYXQiOjE2NTgyNDAxODMsImV4cCI6MTY1ODI0NzM4MywibmFtZSI6IkZWQUdPQ01QIiwiYWRtaW4iOmZhbHNlfQ.XMyFGUC84oh2g3s9-4EkCFwcjP3mSclBbjnz8XvLsnE
Content-Length: 177

{
    "Event": "FWB,LAT,RCS,DEP,ARR,RCF,NFD,DLV,RMP,CAN",
    "Url": "https://www.mycoolsite.com/WebHookST7",
    "Enable": false,
    "Type": "text",
    "AWB": "125"
}
```

If everything is **200 OK**, StarTracking API will return an answer with all the summary information:

```json
{
    "Id": 35,
    "ForwarderIdentifier": "SMECCIEMB",
    "Event": "FWB,LAT,RCS,DEP,ARR,RCF,NFD,DLV,RMP,CAN",
    "Url": "https://www.mycoolsite.com/WebHookST",
    "Token": null,
    "Enabled": false,
    "Type": "json",
    "Psk": null,
    "AWB": null
}
```

In this example, we created a disabled rule to notify all the milestones events to the https://www.mycoolsite.com/WebHookST website.

> Keep in mind:
>	* Type property accepts json, xml or text
>	* Token property (optional) can be only a valid JWT token; please refer to https://jwt.io for more information
>	* Psk property (optional) in case your web API supports preshared key.

## Search Webhook

The API endpoint to return a paged list of all saved webhook configurations

```html
GET /ffw/startracking/routemap/webhook HTTP/1.1
Host: api.startracking.aero
Accept-Encoding: gzip, deflate, br
Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczovL2FwaS5zdGFydHJhY2tpbmcuYWVybyIsInN1YiI6IkZWQUdPQ01QIiwibmJmIjoxNjU4MjQwMTgzLCJpYXQiOjE2NTgyNDAxODMsImV4cCI6MTY1ODI0NzM4MywibmFtZSI6IkZWQUdPQ01QIiwiYWRtaW4iOmZhbHNlfQ.XMyFGUC84oh2g3s9-4EkCFwcjP3mSclBbjnz8XvLsnE
```