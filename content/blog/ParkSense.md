---
title: "ParkSense"
date: 2025-03-01
description: "ParkSense is an IoT system that manage a paid parking network, with automatic payments and live update of parking slot availability."
authors:
    - name: Federico Melis
      link: https://github.com/fedemelis
tags:
  - IoT
  - Sensor
  - Arduino
  - Forecasting
  - Variatonal Autoencoder
  - Bridge
  - Backend
  - Flutter
  - LoRa
published: true
---

# ParkSense

## Brief introduction

ParkSense is an IoT system that manage a paid parking network, with automatic payments and live update of parking slot availability. It is composed by a network of sensor placed in the parking slot, that detect the presence of a car and communicate with a bridge that is connected to the internet. The bridge talks with a VPS that plays the role of beckend server. The system is also composed by a mobile app that allows the user to see the availability of the parking slots and to pay for the parking.

## Architecture overview

The system is composed by the following components:

* **Sensor**: placed in the parking slot, it detects the presence of a car and communicate with the bridge.
* **Microcontroller Sender**: placed in the middle of the parking slot, it collects the information about some changes and send them to the receiver.
* **Microcontroller Receiver**: placed near the bridge, it receives the information from the sender and send them to the bridge.
* **Bridge**: it handles the communication between the sensors and the backend server.
* **Backend server**: it handles the communication between the bridge and the app.
* **App**: it allows the user to see the availability of the parking slots and to start new parking sessions.

![](/images/architecture.png)
```

