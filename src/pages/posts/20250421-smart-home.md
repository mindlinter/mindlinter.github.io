---
layout: ../../layouts/post.astro
title: "Is the grass greener in the IoT world?"
pubDate: 2025-04-21
description: "How hard could it be to add the temperature sensor to your smart home?"
author: ""
isPinned: true
excerpt: "Smart home using Home Assistant is not so easy as it seems. I spent a lot of time on one temperature sensor."
image:
  src:
  alt:
tags: ["iot", "smart home", "home assistant", "temperature sensor", "ble", "esphome", "esp32", "xiaomi", "lywsd03mmc"]
---

I mostly do web development. Previously, it was more backend. Now it is more frontend. 
And I always think that things are better in some other software development areas. For example, I thought that NPM package management was a hell, but once I saw dependencies for a Python project for AI, when a different graphics video card, a different version of drivers requires different dependencies… But that is another story. Today, IoT, mostly about the smart home.

## How hard could it be to add the temperature sensor to your smart home?

There are different approaches for building smart homes. The first one is relying on some 3rd party services. It can be Apple Home, Google Home, or Mi Home. I had experience with Mi Home, and I wasn’t quite happy. The two main reasons for my unhappiness. You are locked with a vendor. And number of sensors and devices is limited. And you are very limited in the customizations. You have a mobile app, which doesn’t give you the best experience.

The second approach for a smart home is the use of Home Assistant. You control everything, you can use any device, and you have unlimited abilities. Indeed, at least you have more control, a bigger list, but still limited supported devices, and a lot of software limitations. But at least you get more freedom.

I decided to try. And decided to try from the small: adding a temperature sensor. The easiest possible task. Yes? But, I spent a lot of hours on one temperature sensor…

### Home server

First of all, you need somewhere to host Home Assistant. I have a home server and I decided to use it. However, the location of the home server doesn’t allow connecting all sensors. The distance is too big. I need a bridge.

### Bridge

I decided to use Bluetooth Low Energy (BLE) sensors. The reason was simple. At least I will be able to connect to Bluetooth with a phone or laptop and troubleshoot the issues. I need the bridge to read the Bluetooth signal value and pass it via Wi-Fi. That is not so easy. The most popular approach for it is the use of ESPHome via ESP32. It requires hosting an additional server, ESPHome. And the configuration of the ESP32 Bluetooth+Wi-Fi module. It is not enough to configure the module. You should flash it with custom binaries. Fortunately, you can do it by air.

### Sensor

I opened the ESPHome sensors list. And selected a sensor that I like visually. Small and simple. Xiaomi LYWSD03MMC. That was a mistake. I should carefully read about it before taking it. The vendors like Xiaomi are trying to protect their devices. They also added encryption for sensor values, like humidity or temperature. It becomes hard to use them without Mi Home. The sensor didn’t work with Home Assistant using Xiaomi's stock firmware. The required bindkey didn’t work. And low-level debugging will be required to figure out the reason. Fortunately, there were 2 custom firmwares. The one is incompatible with the device that I got. Second, did work. But it takes me a while to make it work. I will leave the paragraph with complete instructions, as it requires looking and reading in a few places to figure out how to do it.

### LYWSD03MMC firmware **2.1.1_0159,** using custom firmware

1. You need a [Mi Home](https://play.google.com/store/apps/details?id=com.xiaomi.smarthome&hl=uk) account.
2. You need to register your temperature sensor in your Xiaomi account.
3. You need [Xiaomi Cloud Binder Extractor](https://github.com/PiotrMachowski/Xiaomi-cloud-tokens-extractor). It can be a binary or Python script.
4. You need to run Xiaomi Cloud Binder Extractor and log in using your Xiaomi account. It will ask you login, password, and which server you want to log in to. And it will give you the list of all devices connected to the account, including the device from step 2.
5. You need to [download 2 firmwares](https://github.com/atc1441/ATC_MiThermometer):  [Stock_fw_2.1.1_0159.bin](https://github.com/atc1441/ATC_MiThermometer/blob/master/Stock_fw_2.1.1_0159.bin) (The stock firmware) and [ATC_Exploit.bin](https://github.com/atc1441/ATC_MiThermometer/blob/master/ATC_Exploit.bin) (the exploit allowing you to use a sensor with the Home Assistant). 
6. Open [https://atc1441.github.io/TelinkFlasher.html](https://atc1441.github.io/TelinkFlasher.html) page.
7. Connect via Bluetooth to your sensor.
8. Copy “Device known id”, “Mi Token”, and “Mi Bind Key” from step 4 for your device.
9. Click “Do via Login”. You should get the message about a successful login.
10. Choose the stock firmware file from step 5. You need to flash your device initially with this stock version as firmware versions can be different, even if they have the same number.
11. Click “Start Flashing”.
12. After a few minutes, you should get your device with stock firmware that is ready for patching.
13. Click “Reconnect”, and you should be able to connect to your sensor.
14. Repeat step 4. You need a fresh “Device known id”, “Mi Token”, and “Mi Bind Key” for your device.
15. Copy the value from step 14 to the form.
16. Choose the exploit “ATC_Exploit.bin” file from step 5 as the new firmware.
17. Click “Start Flashing”. After a few minutes, you should get the sensor that should be ready to work with ESPHome
18. If something doesn’t work, just try to repeat the step. I wasn’t able to do it on my first attempt. Bluetooth connection. Problems with the Xiaomi account. It may happen. Just try again.

Many thanks to [Aaron Christophel](https://github.com/atc1441) and [Piotr Machowski](https://github.com/PiotrMachowski), who made this exploit and the tools to extract Xiaomi secrets.

I want to add a security consideration from myself. Previous Xiaomi sensor firmware revisions, as well as firmware after the patching, **allow anyone to flash your LYWSD03MMC Xiaomi sensor with any firmware**. You don’t need a Xiaomi account to do it. You should just be near the sensor with your phone or laptop. It seems that Xiaomi closed this ability in recent firmware. But, we can’t use this sensor together with the latest stock Xiaomi firmware with Home Assistant. And that is why we need the Xiaomi Cloud Binder Extractor only for recent sensor revisions. 
This vulnerability means that intruders can brick your sensor. Or they can add some code that will send wrong values, trying to trigger some automation in your Home Assistant. Not a huge vulnerability, but still a vulnerability!

## Afterward

It was required to configure Docker Compose for Home Assistant and ESPHome, flash the ESP32 module, flash the sensor, and write the configuration to make it work together. I spent about 8 hours on it and 1 hour on this blog post. Next time it will be faster, as I have new knowledge and made notes. But still, not less than a few hours. And all these actions to have temperature and humidity values on the web page… Is it worth it? 

It makes Home Assistant, sensors, and devices around it almost unusable for a person without any technical knowledge. And that is obvious, why many people choose Apple Home or something similar despite limitations.

The grass in the IoT and smart homes software development world doesn’t look greener now. The first, high-level attempt and a lot of bugs, incompatibilities, bloated architecture, and security problems. Yes, that is possible to get used to it. But it looks wrong and broken… Probably, like all software development. 😄