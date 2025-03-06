---
title: "ParkSense"
date: 2025-03-01
description: "ParkSense is an IoT system that manage a paid parking network, with automatic payments and live update of parking slot availability."
authors:
    - name: Federico Melis
      link: https://github.com/fedemelis
    - name: Biagio Grimolizzi
    - name: Emanuele Prato
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

![](https://fedemelis.github.io/img/architecture.png)

# 

## Sensor

The sensor we used is a HC-SR04 ultrasonic sensor. It can detect the distance between the sensor and an object in front of it.
It has 4 pins:
* **VCC**: 5V
* **Trig**: trigger pin
* **Echo**: echo pin
* **GND**: ground

{{< callout emoji="💡" >}}
  We used a particular library for the ultrasonic sensor; the library is called `NewPing` and allow us to use one single pin for both the trigger and the echo.
{{< /callout >}}

## Microcontroller (Sender)

The MC we used is an Arduino Uno and it handles the state switching of the parking slot. It also make use of the LoRa E220-900T22D module to communicate with the receiver.

![](https://fedemelis.github.io/img/arduino-sender.png)

## Microcontroller (Receiver)

This MC is also an Arduino Uno and it receives message from all the senders in the parking network. It also make use of the LoRa E220-900T22D. One it receives a message, it sends it to the bridge via serial communication.

{{< callout emoji="📡" >}}
  We chosed the LoRa module because it has a long range and low power consumption.
{{< /callout >}}

## Bridge

The bridge is a laptop (for the prototype) that is connected to the internet. It obviously should be a Raspberry Pi or something similar but we do not have a raspberry at the moment.
The bridge receives the messages from the receiver and is the one that communicates with the server and trigger the state change of the parking slot.

![](https://fedemelis.github.io/img/bridge.png)


## Backend server

The backend server is a VPS that is connected to the internet. It is the one that communicates with the bridge and the app. 



