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



#### Header Items

HeaderItems property is mandatory when used with rules of type Email; it allows to customize the subject according to the client's needs. 

| Header Name | Description       |
| :---------: | ----------------- |
|     **AWB** | Awb Number        |
|     **MIL** | Milestone         |
|     **NTF** | Notification Type |
|     STN     | Event Station     |
|     RTG     | Routing           |
|     RMT     | RM Type           |
|     AGT     | Agent Code        |
|     BRA     | Agent Station     |


{{< alert title="Note" >}}
The minimum requirement is:<BR>
"HeaderItems": "AWB,MIL,NTF"
{{< /alert >}} 


### Use Case #2 (Alert of type "Missed Event")
As a Freight Forwarder, I want to receive a notification when a chosen event does not occur.
In this case, I want to receive a notification in case the planned departure of a leg doesn't happen.

```http
POST /api.startracking/ffw/startracking/routemap/eventconfignotifier HTTP/1.1
Host: dev.cargostart.tech
Accept: application/json, text/plain, */*
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
Authorization: Bearer {{BEARER TOKEN}}
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

{{< alert title="Note" >}}Missed Eveent works only for CiQ Routemap.{{< /alert >}}

### Use Case #3 (Alert of type "Proactive")
As a Freight Forwarder, I want to be notified only when a real problem occurs. 
In this example, using the Proactive Milestone, Star Tracking will notify the user that the departure message did not occur within a user custom defined interval (e.g. 240 minutes).

```http
POST /api.startracking/ffw/startracking/routemap/eventconfignotifier HTTP/1.1
Host: dev.cargostart.tech
Accept: application/json, text/plain, */*
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
Authorization: Bearer {{BEARER TOKEN}}
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

Setting the ChannelType property to **Url** allows the full B2B event notification. StarTracking will feed the endpoint provided with an **event payload**.


{{< alert title="Note" >}}
The **NotifyTo** property must have **unique GUID** generated by CargoStart when you provided your API WebServer address and optional headers:
{{< /alert >}}
**STEP ONE**<br>
Notify StarTracking support team with my API endpoint and header values:
        
    e.g.
    https://www.acmeforwarder.com/startracking

    Headers: apiKey: XXXXXXXX-4A01-4924-A6B7-F72440DD07DE

**STEP TWO**<br>
StarTracking team provides a GUID to use in the **NotifyTo** property

### Use Case #1 (Alert of type "Event")

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

{{< alert title="Note" >}}
[EventNotifier OpenAPI Client](https://github.com/cargostart/EventNotifier) defines the endpoint that accepts the StarTracking notification payload. 
{{< /alert >}}

