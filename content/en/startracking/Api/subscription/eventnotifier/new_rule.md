---
categories: ["API"]
tags: ["api", "EventNotifier"] 
title: "Create a new Rule"
linkTitle: "New Rule"
date: 2022-07-19
type: docs
weight: 10
description: >
    Everything starts by creating a Rule; Lets set some examples:
---

## Channel Type: EMAIL

### Use Case #1 (Alert of type "Event")
As a Freight Forwarder, you want to notify your JFK local office when the shipment has arrived at destination. 

```http
POST /api.startracking/ffw/startracking/routemap/eventconfignotifier HTTP/1.1
Host: dev.cargostart.tech
Accept: application/json, text/plain, */*
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
Authorization: Bearer {{BEARER TOKEN}}
Content-Type: application/json;charset=UTF-8
Content-Length: 341

{
    "ChannelType": "Email",
    "AirlinePrefix": "*",
    "Event": "NFD",
    "NotifyTo": "jfk_station@acme.com",
    "HeaderItems": "AWB,MIL,NTF",
    "FormatType": "Html",
    "EventAlert": true,
    "Destination": "JFK",
    "Enabled": false
}
```

We can decide to apply the rule for a specific carrier

```http
POST /api.startracking/ffw/startracking/routemap/eventconfignotifier HTTP/1.1
Host: dev.cargostart.tech
Accept: application/json, text/plain, */*
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
Authorization: Bearer {{BEARER TOKEN}}
Content-Type: application/json;charset=UTF-8
Content-Length: 341

{
    "ChannelType": "Email",
    "AirlinePrefix": "020",
    "Event": "NFD",
    "NotifyTo": "jfk_station@acme.com",
    "HeaderItems": "AWB,MIL,NTF",
    "FormatType": "Html",
    "EventAlert": true,
    "Destination": "JFK",
    "Enabled": false
}
```

or notify only a specific full AWB number in case we want to monitor only a single shipment.

```http
POST /api.startracking/ffw/startracking/routemap/eventconfignotifier HTTP/1.1
Host: dev.cargostart.tech
Accept: application/json, text/plain, */*
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
Authorization: Bearer {{BEARER TOKEN}}
Content-Type: application/json;charset=UTF-8
Content-Length: 341

{
    "ChannelType": "Email",
    "AirlinePrefix": "020",
    "AwbNumber": "12345675",
    "Event": "NFD",
    "NotifyTo": "jfk_station@acme.com",
    "HeaderItems": "AWB,MIL,NTF",
    "FormatType": "Html",
    "EventAlert": true,
    "Destination": "JFK",
    "Enabled": false
}
```

### Use Case #2 (Alert of type "Missed Event")
As a Freight Forwarder, I want to receive a notification when a chosen event does not occur.
In this case, I want to receive a notification in case the planned departure of a leg doesn't happen.

```http
POST /api.startracking/ffw/startracking/routemap/eventconfignotifier HTTP/1.1
Host: dev.cargostart.tech
Accept: application/json, text/plain, */*
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczovL2Rldi5jYXJnb3N0YXJ0LnRlY2giLCJzdWIiOiJFT0xfQ01QIiwibmJmIjoxNjYwODA3MjA3LCJpYXQiOjE2NjA4MDcyMDcsImV4cCI6MTY2MDgxMDgwNywibmFtZSI6IkVPTF9DTVAiLCJhZG1pbiI6ZmFsc2V9.VsCws-2nqxpLVS9j_Q0dlisRYzkWC2_S5yA8gAfkqcI
Content-Type: application/json;charset=UTF-8
Content-Length: 236

{
    "ChannelType": "Email",
    "AirlinePrefix": "*",
    "Event": "DEP",
    "NotifyTo": "operations@acme.com",
    "HeaderItems": "AWB,MIL,NTF",
    "FormatType": "Html",
    "MissedEventAlert": true,
    "Enabled": false
}
```

> Note: Missed Eveent works only for CiQ Routemap

### Use Case #3
As a Freight Forwarder, I want to be notified only when a real problem occurs. 
In this example, using the Proactive Milestone, Star Tracking will notify the user that the departure message did not occur within a user custom defined interval (e.g. 240 minutes).

```http
POST /api.startracking/ffw/startracking/routemap/eventconfignotifier HTTP/1.1
Host: dev.cargostart.tech
Accept: application/json, text/plain, */*
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczovL2Rldi5jYXJnb3N0YXJ0LnRlY2giLCJzdWIiOiJFT0xfQ01QIiwibmJmIjoxNjYwODA3MjA3LCJpYXQiOjE2NjA4MDcyMDcsImV4cCI6MTY2MDgxMDgwNywibmFtZSI6IkVPTF9DTVAiLCJhZG1pbiI6ZmFsc2V9.VsCws-2nqxpLVS9j_Q0dlisRYzkWC2_S5yA8gAfkqcI
Content-Type: application/json;charset=UTF-8
Content-Length: 261

{
    "ChannelType": "Email",
    "AirlinePrefix": "*",
    "Event": "DEP",
    "NotifyTo": "operations@acme.com",
    "HeaderItems": "AWB,MIL,NTF",
    "FormatType": "Html",
    "ProActiveAlert": true,
    "ProActiveTime": 240,
    "Enabled": false
}
```

## Channel Type: URL (API)

As a Freight Forwarder I want to be notified for all my shipments, only the actual events of type DEP, ARR, NFD and DLV
 
```http
POST /ffw/startracking/routemap/eventconfignotifier HTTP/1.1
Host: api.startracking.aero
Accept: application/json, text/plain, */*
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
Authorization: Bearer {{BEARER TOKEN}}
Content-Type: application/json;charset=UTF-8
Content-Length: 355

{
    "ChannelType": "Url",
    "NotifyTo": "342DE97C-C63C-475D-A4A8-7B52F43D154E",
    "HeaderItems": "",
    "FormatType": "Json",
    "AirlinePrefix": "*",
    "AwbNumber": "",
    "Event": "DEP,ARR,NFD,DLV",
    "ProActiveAlert": false,
    "ProActiveTime": 0,
    "MissedEventAlert": false,
    "EventAlert": true,
    "Enabled": true
}
```

> ChannelType must be set to **Url**<BR>
> NotifyTo have to report the **unique GUID** generated by CargoStart when you provided your API WebServer address and headers:
> 
> e.g. 
> https://www.acmeforwarder.com/startracking
>
> Headers: apiKey: XXXXXXXX-4A01-4924-A6B7-F72440DD07DE


The response is 200 OK: 

```json
{
    "ChannelType": "Url",
    "NotifyTo": "342DE97C-C63C-475D-A4A8-7B52F43D154E",
    "HeaderItems": "",
    "FormatType": "Json",
    "Id": 189,
    "ForwarderIdentifier": "SMECCIEOL",
    "AirlinePrefix": "*",
    "AwbNumber": "",
    "Event": "DEP,ARR,NFD,DLV",
    "ProActiveAlert": false,
    "ProActiveTime": 0,
    "MissedEventAlert": false,
    "EventAlert": true,
    "AgentCode": null,
    "AgentCass": null,
    "Origin": null,
    "Destination": null,
    "IgnoreStation": null,
    "Enabled": true
}
```

From now on all the actual Events DEP, ARR, NFD, DLV will be POSTed to  https://www.acmeforwarder.com/startracking

```http
POST /startracking HTTP/1.1
apiKey: XXXXXXXX-4A01-4924-A6B7-F72440DD07DE
Content-Type: application/json
Content-Length: 820

{
    "IdMessage": "AiLnMVU0GkumL8aQiXC5A/ARR",
    "AirWaybillPrefix": "020",
    "AirWaybillNumber": "27032353",
    "ForwarderIdentifier": "SMECCIXXX",
    "AgentCode": "0000000",
    "AgentCass": "0000",
    "AgentStation": "MIL",
    "Type": "Event",
    "Event": "ARR",
    "EventStatus": "Update",
    "AirportOfEvent": "BRU",
    "AirportOfOrigin": "SWK",
    "AirportOfDestination": "DSS",
    "CarrierCode": "LH",
    "FlightNumber": "7674S",
    "PiecesReported": 4,
    "TotalShipmentPieces": 4,
    "WeightReported": null,
    "WeightCode": null,
    "MilestoneReportedLocalTimeStamp": "2022-06-24T12:00:00",
    "MilestoneReportedUtcTimeStamp": "2022-06-24T16:00:00+00:00",
    "isRM": true,
    "TavGap": null,
    "PlannedLocalTimeStamp": null,
    "PlannedUtcTimeStamp": null
}
```

[EventNotifier OpenAPI Client](https://github.com/cargostart/EventNotifier)