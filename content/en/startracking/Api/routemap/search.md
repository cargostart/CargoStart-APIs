---
categories: ["API"]
tags: ["api", "routemap"] 
title: "Search"
linkTitle: "Search"
date: 2022-07-19
type: docs
weight: 10
description: >
  Search Routemap
---
The API endpoints to retrieve all those Route Maps is

```http
POST /ffw/startracking/routemap HTTP/1.1
Host: api.startracking.aero
Accept: application/json, text/json
Content-Type: application/json
Authorization: Bearer {{BEARER TOKEN}}
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
