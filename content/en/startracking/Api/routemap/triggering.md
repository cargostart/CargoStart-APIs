---
categories: ["API"]
tags: ["api", "routemap"] 
title: "Triggering"
linkTitle: "Triggering"
date: 2022-07-19
type: docs
weight: 30
description: >
  Triggering a CiQ Route Map
---
StarTracking always does its best to provide as soon as possible a CiQ Route Map. 

> To be sure to receive an updated Cargo iQ Routemap as soon as an operator finalizes a booking and enter the information in its TMS application, a call to the SME method should be done:

The request body is straightforward, all you need is to provide the full AWB # and the full IATA Agent Code:

```http
POST /ffw/startracking/routemap/sendsme HTTP/1.1
Host: api.startracking.aero
Authorization: Bearer {{BEARER TOKEN}}
Content-Type: application/json
Content-Length: 109

{
  "AirlinePrefix": "999",
  "AwbNumber": "12345675",
  "AgentCode": "3847361",
  "AgentCass": "0011"
}
```

In almost realtime, the AWB is sent to the Carrier, and a Route Map is returned.