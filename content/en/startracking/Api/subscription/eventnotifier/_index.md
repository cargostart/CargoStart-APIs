---
categories: ["API"]
tags: ["api", "Webhook"] 
title: "Event Notifier"
linkTitle: "Event Notifier"
date: 2022-07-19
type: docs
weight: 40
description: >
---
> We assume you are already familiar with our API authentication; if not please watch before:
> * **[CargoStart API a Sneak Peek introduction](/startracking/getting-started/#a-sneak-peek-introduction)**
> * **[StarTracking Authentication and Authorization](/startracking/api/authentication/)**

One of the most requested features was to obtain all the events in real-time.
Our new and flexible engine allows you to customize your real-time notifications according to your needs.

Fine-tuning the setting rule correctly, we can optimize our system to receive only the notifications we need.

In StarTracking Event Notifier there are three distinct notifications:
- Event notification, to get a notification at the moment an event occurs.
- Missed Event, to get a notification at the moment of an event that didn't occur.
- Proactive notification, to set a customized value in minutes and ensure you do not get "false positive" notifications.

