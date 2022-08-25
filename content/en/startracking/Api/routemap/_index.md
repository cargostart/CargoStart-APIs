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
> We assume you are already familiar with our and authentication; if not please watch before:
> * **[CargoStart API a Sneak Peek introduction](/startracking/getting-started/#a-sneak-peek-introduction)**
> * **[StarTracking Authentication and Authorization](/startracking/api/authentication/)**

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


