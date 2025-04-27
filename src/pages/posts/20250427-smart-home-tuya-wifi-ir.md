---
layout: ../../layouts/post.astro
title: "Unmature Smart Home: Tuya WiFi IR and Home Assistant"
pubDate: 2025-04-21
description: "IR remote control for AC and Home Assistant integration with Tuya."
author: ""
isPinned: true
excerpt: "Smart home using Home Assistant is not so easy as it seems. I spent a lot of time on one temperature sensor."
image:
  src:
  alt:
tags: ["iot", "smart home", "home assistant", "xiaomi", "tuya", "wifi", "ir"]
---

Another weekend, another smart device. Or not very smart.

Previously, I managed to configure the Xiaomi temperature sensor to work with ESPHome and Home Assistant. Now, I want to use it. I live on the west side of the building and sleep too long. Summer is coming! Wouldn’t it be nice if my smart home could be able to turn on or off the AC while I am sleeping in the morning?

I bought “**Zigbee WiFi Remote Control Universal Infrared Tuya Smart Home Remote Controller for TV DVD Works For Google Home**”. Yes, it is the Aliexpress title. Indeed, it is a WiFi Zigbee Bluetooth(yes, the manual says that Bluetooth is also included) IR Hub to control your IR devices.

The device works with the Smart Home fine. A few clicks on your mobile and you are able to turn on or off your AC. 

But again, not with the Home Assistant. Reading GitHub instruction, setting up HACS, setting up Local Tuya, trying to add a device, reading blogs, reading GitHub issues, reconfiguring Docker Home Assistant to have a different network, `tinytuya`, Tuya Developer portal, turning on and off, reading blogs, network checking, ports checking, Mikrotik configuration check, and giving up…

Why is it so hard? Why doesn’t it work as expected? Is it possible at all?

As a temporary solution, I integrated Home Assistant with the official Tuya application. I can’t control IR from the Home Assistant. There is no such option. Tuya added support for the device, but it is limited. I can only add a scene in the Tuya Smart application(e.g., turn on the AC) and start that scene from the Home Assistant. I have the first automation. Not ideal, jury-rigged, but test run was successful.

Now, I am waiting for the summer hot days. And thinking about Apple Home Kit…