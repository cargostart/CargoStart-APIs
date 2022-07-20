---
categories: ["API"]
tags: ["api", "routemap"] 
title: "Retrieve"
linkTitle: "Retrieve"
date: 2022-07-19
type: docs
weight: 20
description: >
  Retrieve a single Routemap
---
Once you know which AWB # you want to retrieve you can do that merely adding the awb# to the route map endpoint,

```http
POST /ffw/startracking/routemap HTTP/1.1
Host: api.startracking.aero
Accept: application/json, text/json
Content-Type: application/json
Authorization: {{tokenid}}
Content-Length: 59

{
    "AirlinePrefix": "057",
    "AwbNumber": "06726510"
}
```
### Anatomy of a Routemap Response


```json
{
    "TotalItems": 1,
    "TotalPages": 1,
    "PageSize": 100,
    "CurrentPage": 1,
    "Items": [
        {
            "RMRank": 30,
            "SRRank": 20,
            "IsRM": true,
            "LastUpdate": "2022-07-19T13:38:14",
            "Shipment": {
                "AirlinePrefix": "020",
                "AwbNumber": "27032331",
                "Routing": {
                    "Origin": "SWK",
                    "Destination": "MAA"
                },
                "Total": {
                    "NoOfPieces": 1,
                    "WeightCode": "K",
                    "Weight": 84.0,
                    "VolumeCode": "CM",
                    "Volume": 0.24
                }
            },
            "DeliveryDate": {
                "Utc": "2022-07-22T04:20:00Z",
                "Local": "2022-07-22T09:50:00"
            },
            "ReceiptDate": {
                "Utc": "2022-07-19T17:00:00Z",
                "Local": "2022-07-19T19:00:00"
            },
            "ProductCode": "YNZ",
            "IsRoadFeederService": false,
            "Status": "Booked",
            "IsReplanned": false,
            "RoutingIsReplanned": false,
            "OriginState": 1,
            "RoutingState": 2,
            "DestinationState": 2,
            "Origin": {
                "Status": "Partial",
                "Warnings": true
            },
            "Routing": {
                "Status": "Planned",
                "Warnings": null
            },
            "Destination": {
                "Status": "Planned",
                "Warnings": null
            },
            "CreationDate": {
                "Utc": "2022-07-19T13:38:14Z",
                "Local": "2022-07-19T15:38:14"
            }
        }
    ]
}
```

You can see many parts are similar to the Routemap Search response; we will concentrate only to the new properties.

The Routemap milestone is separated into three different cycles:
* OriginCycle 
* RoutingCycle
* DestinationCycle

Every Cycle has a collection of specific Milestones:

#### OriginCycle
Here you can find all the origin milestones, every with its information on the Status, the Station of Origin, the Planned and the Actual time 
*	FWB 
*	LAT
*	RCS


#### RoutingCycle
Essentially a collection of all the flight numbers, from origin to destination; for every flight there are the following milestones:
*	DEP
* ARR
* RCF

#### DestinationCycle
* NFD
* DLV

Any Cycle has the Status property that can be:

*	Planned
*	Partial
*	Completed

Milestone Status property can be
*	Missing, Scheduled Time occurred, but no Milestone message received
*	Ko, Milestone message sent late
*	Ok, Milestone message arrived in time 

They summarize all the milestones inside the specific Cycle.

#### Routemap with its History

In case you need all the life cycle of a Routemap, you can add the "/history" word to the call: 

GET  /ffw/startracking/routemap/{AWB}/history

This call returns the selected route map and all its snapshots. 

> Keep in mind that the history data are available only for 30 days from the route map creation. 
