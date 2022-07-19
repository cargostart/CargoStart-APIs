---
categories: ["API"]
tags: ["api", "routemap"] 
title: "Routemap"
linkTitle: "Routemap"
date: 2022-07-19
type: docs
weight: 20
description: >
  In short, a Route Map summarizes - in real-time - the whole life cycle of an air cargo shipment, from booking to delivery.
---
We assume you are already familiar with our API and authentication; if not please watch before:
* **[CargoStart API a Sneak Peek introduction](/startracking/getting-started/#a-sneak-peek-introduction)**
* **[StarTracking Authentication and Authorization](/startracking/api/authentication/)**

Without any doubt, the Route Map concept is the central pillar of our Startracking service.

In this chapter, we will concentrate on how to search and retrieve those Route maps using the CargoStart API.

A StarTracking Route Map comes in two flavours:
* CargoIQ Route Map
* Simple Route Map

## CiQ Route Map

Essentially, the state of the art of a Route Map. 

When a freight forwarder finalizes the booking via phone, email or web with an airline participating the IATA Cargo iQ program, a Route Map is created and available in just a few minutes with all the planned events, from the acceptance of the delivery to the shipments. 

Cargo iQ Route Map is continuously updated, from every booking replan to every significant milestone achieved.

## Simple Route Map

This is our simplified yet powerful Route Map. It is fed by the Status Update messages provided by carriers; this Route Map does not include the planned events, but just the current ones.

Both Route Maps sport the “snapshot” feature; any changes are stored as a snapshot, so all the history can be reviewed if needed.

## Search Routemap

The API endpoints to retrieve all those Route Maps is

```http
POST /ffw/startracking/routemap HTTP/1.1
Host: api.startracking.aero
Accept: application/json, text/json
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczovL2FwaS5zdGFydHJhY2tpbmcuYWVybyIsInN1YiI6IklUQUxJQU5TUEVEX0FQSSIsIm5iZiI6MTY1ODIzNjUxMCwiaWF0IjoxNjU4MjM2NTEwLCJleHAiOjE2NTgyNDAxMTAsIm5hbWUiOiJJVEFMSUFOU1BFRF9BUEkiLCJhZG1pbiI6ZmFsc2V9.p_e23mQy6wUVWDm0Q8NDrDklc0roIPCMAqEkv5GNxpE
Content-Length: 104

{
    "CreationDate": {
        "StrStartDate": "19/07/2022",
        "StrEndDate": "19/07/2022"
    }
}
```

we obtain

```json
{
    "TotalItems": 2,
    "TotalPages": 1,
    "PageSize": 100,
    "CurrentPage": 1,
    "Items": [
        {
            "RMRank": 0,
            "SRRank": 125,
            "IsRM": false,
            "LastUpdate": "2022-07-05T10:00:59",
            "Shipment": {
                "AirlinePrefix": "047",
                "AwbNumber": "08014355",
                "Routing": {
                    "Origin": "SWK",
                    "Destination": "CCS"
                },
                "Total": {
                    "NoOfPieces": 8,
                    "WeightCode": "K",
                    "Weight": 1058.7,
                    "VolumeCode": null,
                    "Volume": null
                }
            },
            "DeliveryDate": null,
            "ReceiptDate": {
                "Utc": "2022-07-01T16:06:00Z",
                "Local": "2022-07-01T17:06:00"
            },
            "ProductCode": null,
            "IsRoadFeederService": false,
            "Status": "OnAir",
            "IsReplanned": false,
            "RoutingIsReplanned": false,
            "OriginState": 1,
            "RoutingState": 1,
            "DestinationState": 2,
            "Origin": {
                "Status": "Completed",
                "Warnings": true
            },
            "Routing": {
                "Status": "Partial",
                "Warnings": true
            },
            "Destination": {
                "Status": "Planned",
                "Warnings": null
            },
            "CreationDate": {
                "Utc": "2022-07-01T16:10:39Z",
                "Local": "2022-07-01T18:10:39"
            }
        },
        {
            "RMRank": 0,
            "SRRank": 280,
            "IsRM": false,
            "LastUpdate": "2022-07-03T12:25:04",
            "Shipment": {
                "AirlinePrefix": "176",
                "AwbNumber": "39340103",
                "Routing": {
                    "Origin": "BLQ",
                    "Destination": "DAC"
                },
                "Total": {
                    "NoOfPieces": 1,
                    "WeightCode": "K",
                    "Weight": 41.8,
                    "VolumeCode": null,
                    "Volume": null
                }
            },
            "DeliveryDate": {
                "Utc": "2022-07-03T12:24:00Z",
                "Local": "2022-07-03T18:24:00"
            },
            "ReceiptDate": {
                "Utc": "2022-07-01T10:38:00Z",
                "Local": "2022-07-01T12:38:00"
            },
            "ProductCode": null,
            "IsRoadFeederService": false,
            "Status": "AtDestination",
            "IsReplanned": false,
            "RoutingIsReplanned": false,
            "OriginState": 1,
            "RoutingState": 1,
            "DestinationState": 1,
            "Origin": {
                "Status": "Completed",
                "Warnings": true
            },
            "Routing": {
                "Status": "Completed",
                "Warnings": true
            },
            "Destination": {
                "Status": "Completed",
                "Warnings": true
            },
            "CreationDate": {
                "Utc": "2022-07-01T10:39:29Z",
                "Local": "2022-07-01T12:39:29"
            }
        }
    ]
}
```

> CreationDate, can be replaced by DeliveryDate or ReceiptDate.

### Retrieve all the shipments of a carrier:

```json
{
    "CreationDate": {
        "StrStartDate": "19/07/2022",
        "StrEndDate": "23/07/2022"
    },
    "AirlinePrefix": "020"
}
```

### Specific AirWaybill

```json
{
    "CreationDate": {
        "StrStartDate": "19/07/2022",
        "StrEndDate": "23/07/2022"
    },
    "AirlinePrefix": "020",
    "AwbNumber": "58014261"

}
```

### Specific Routing
```json
Or a Specific Routing
{
     "CreationDate": {
        "StrStartDate": "19/07/2022",
        "StrEndDate": "23/07/2022"
    },
    "Routing": {
        "Origin": "MIA",
        "Destination": "MXP"
    }
}
```
### A set of Shipment Status
```json
{
   "CreationDate": {
        "StrStartDate": "19/07/2022",
        "StrEndDate": "23/07/2022"
    },
    "Status": [
        "OnAir",
        "Booked"
    ]
}
```

> Possible shipment Status are **OnAir**, **Booked**, **Accepted**, **AtDestination**, **Cancelled**

### Record Paging

Record Paging is supported by default; 

```json
{
    "TotalItems": 16,
    "TotalPages": 1,
    "PageSize": 100,
    "CurrentPage": 1,
    "Items": [
      {

      }.
      {

      },
      .....
    ]
}
```

PageSize property is set to 100 by default; in case you obtain a greater **TotalItems** count you can retrieve the second page of a resultset adding the **CurrentPage** property set as 2:

```json
{
   "CreationDate": {
        "StrStartDate": "19/07/2022",
        "StrEndDate": "23/07/2022"
    },
    "CurrentPage": 2
}
```

### Sort

The Search request can be sorted by:
* DeliveryDate
* Status
* CreationDate
* Origin
* Destination
* AwbNumber

> Use + or – preceding the sort key to retrieve the records in ascending or descending order

```json
{
     "CreationDate": {
        "StrStartDate": "19/07/2022",
        "StrEndDate": "23/07/2022"
    },
    "statusSelected": "OnAir",
    "Sort":"-ReceiptDate",
    "CurrentPage": 2
}
```

> Multiple Sort keys are supported using space between keywords:

```json
{
     "CreationDate": {
        "StrStartDate": "19/07/2022",
        "StrEndDate": "23/07/2022"
    },
    "statusSelected": "OnAir",
    "Sort":"-ReceiptDate +Origin +AwbNumber",
    "CurrentPage": 2
}
```

### Anatomy of a Routemap Search Response

A response is formed by one Header section and one array of Items.

```json
{
    "TotalItems": 16,
    "TotalPages": 1,
    "PageSize": 100,
    "CurrentPage": 1,
    "Items": [
      {

      }.
      {

      },
      .....
    ]
}
```

The header contains all the related properties for [Record Paging](#record-paging):

* "TotalItems": 16,
* "TotalPages": 1,
* "PageSize": 100,
* "CurrentPage": 1

In the items array, comes all the single shipments

```json
{
    "RMRank": 0,
    "SRRank": 125,
    "IsRM": false,
    "LastUpdate": "2022-07-05T10:00:59",
    "Shipment": {
        "AirlinePrefix": "047",
        "AwbNumber": "08014355",
        "Routing": {
            "Origin": "SWK",
            "Destination": "CCS"
        },
        "Total": {
            "NoOfPieces": 8,
            "WeightCode": "K",
            "Weight": 1058.7,
            "VolumeCode": null,
            "Volume": null
        }
    },
    "DeliveryDate": null,
    "ReceiptDate": {
        "Utc": "2022-07-01T16:06:00Z",
        "Local": "2022-07-01T17:06:00"
    },
    "ProductCode": null,
    "IsRoadFeederService": false,
    "Status": "OnAir",
    "IsReplanned": false,
    "RoutingIsReplanned": false,
    "OriginState": 1,
    "RoutingState": 1,
    "DestinationState": 2,
    "Origin": {
        "Status": "Completed",
        "Warnings": true
    },
    "Routing": {
        "Status": "Partial",
        "Warnings": true
    },
    "Destination": {
        "Status": "Planned",
        "Warnings": null
    },
    "CreationDate": {
        "Utc": "2022-07-01T16:10:39Z",
        "Local": "2022-07-01T18:10:39"
    }
}
```

There are many pieces of information, the most important are 

#### the Shipment Section

```json
"Shipment": {
        "AirlinePrefix": "047",
        "AwbNumber": "08014355",
        "Routing": {
            "Origin": "SWK",
            "Destination": "CCS"
        },
        "Total": {
            "NoOfPieces": 8,
            "WeightCode": "K",
            "Weight": 1058.7,
            "VolumeCode": null,
            "Volume": null
        }
    }
```
#### the Status property

```json
"Status": "OnAir"
```

> the Status property of Origin, Routing and Destination sections set to "Planned", "Partial" or "Completed".

```json
"Origin": {
        "Status": "Completed",
        "Warnings": true
    },
    "Routing": {
        "Status": "Partial",
        "Warnings": true
    },
    "Destination": {
        "Status": "Planned",
        "Warnings": null
    },
```

#### Some Boolean properties worth to know:

* **IsRM**: when false SimpleRoutemap, true if CiQ Route Map
* **IsRoadFeederService**: if RFS operates at least one leg of the shipment
* **IsReplanned**: if there was a change with pieces, weight or volume
* **RoutingIsReplanned**:  if there was a routing change after the first booking

## Retrieve a single Routemap

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

### Triggering a CiQ Route Map

StarTracking always does its best to provide as soon as possible a CiQ Route Map. 

> To be sure to receive an updated Cargo iQ Routemap as soon as an operator finalizes a booking and enter the information in its TMS application, a call to the SME method should be done:

The request body is straightforward, all you need is to provide the full AWB # and the full IATA Agent Code:

```http
POST /ffw/startracking/routemap/sendsme HTTP/1.1
Host: api.startracking.aero
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczovL2FwaS5zdGFydHJhY2tpbmcuYWVybyIsInN1YiI6IkZWQUdPQ01QIiwibmJmIjoxNjU4MjQwMTgzLCJpYXQiOjE2NTgyNDAxODMsImV4cCI6MTY1ODI0NzM4MywibmFtZSI6IkZWQUdPQ01QIiwiYWRtaW4iOmZhbHNlfQ.XMyFGUC84oh2g3s9-4EkCFwcjP3mSclBbjnz8XvLsnE
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