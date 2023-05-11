<img align=right width="200" src="docs/img/sick-logo.jpg"/> 

LiDAR API Documentation and Examples
---

![#f03c15](https://placehold.co/15x15/f03c15/f03c15.png) `This document is on DRAFT stage!` ![#f03c15](https://placehold.co/15x15/f03c15/f03c15.png)


This description covers all possibilities to work with the following sensors. 

- [multiScan100](https://www.sick.com/de/en/lidar-sensors/3d-lidar-sensors/multiscan100/c/g574914)  <img style="right;"  width="45" src="docs/img/multiScan.png"/>

- picoScan150

... you have your sensor on hand: [Kick start here](#getting-started-to-work-with-a-sensor) :rocket:

<br/>
<br/>

# Table of content

- [Table of content](#table-of-content)
- [Introduction](#introduction)
  - [Read or write sensor parameters](#1-read-or-write-sensor-parameters)
  - [Receive event-driven measurement data streaming](#2-receive-event-driven-measurement-data-streaming)
- [General information](#general-information)
  - [Drivers and SDKs](#drivers-and-sdks)
  - [Examples](#examples)
  - [Default IP address](#default-ip-address)
- [Measurement Data Streaming - Comparison and choice](#measurement-data-streaming---comparison-and-choice)
- [Device  configuration - Comparison and choice](#device--configuration---comparison-and-choice)
- [Getting started to work with a sensor](#getting-started-to-work-with-a-sensor)
  - [:zero: Prerequisites](#zero-prerequisites)
  - [:one: See scan data on sensor web server](#one-see-scan-data-on-sensor-web-server)
  - [:two: Decide how you want to work with the device](#two-decide-how-you-want-to-work-with-the-device)
- [FAQ \& Glossary](#faq--glossary)

<br/>
<br/>

# Introduction

The LiDAR API documentation differentiates between two communication concepts. For both cases there are multiple ways to work with the sensor.

<br/>

## 1. Read or write sensor parameters
  - [REST](docs/documentation-rest.md)
  - [CoLa A](docs/documentation-cola.md)
  - [CoLa B](docs/documentation-cola.md)

Communication concept of sensor configuration:

```mermaid
sequenceDiagram
    client->>sensor: set parameter1
    sensor-->>client: acknowledge parameter1
    client->>sensor: set parameter2
    sensor-->>client: acknowledge parameter2
    client->>sensor: ...
```
<br/>

## 2. Receive event-driven measurement data streaming

  - [Compact](docs/documentation-msgpack-compact.md)
  - [MSGPACK](docs/documentation-msgpack-compact.md)
  - [WebSocket](docs/documentation-websocket.md)

Communication concept of measurement data streaming:

```mermaid
sequenceDiagram
    client->>sensor: enable measurement data streaming
    sensor-->>client: acknowledge measurement data streaming
    client->>sensor: measurement data packet [0]
    client->>sensor: measurement data packet [1]
    client->>sensor: measurement data packet [...]
```

<br/>
<br/>

# General information

## Drivers and SDKs

<img align=right width="200" src="docs/img/ROS-logo.png"/> 

For complete drivers instead of single telegrams, the following options are available:

- [ROS drivers](https://github.com/SICKAG/sick_scan_xd)
- [ROS2 drivers](https://github.com/SICKAG/sick_scan_xd)
- [Python drivers](https://github.com/SICKAG/sick_scan_xd)
- [C++ drivers](https://github.com/SICKAG/sick_scan_xd)

## Examples

All available examples can be found [here](examples/).

## Default IP address

The default IP address for the sensors (if not specified different is `192.168.0.1`)

<br/>
<br/>

# Measurement Data Streaming - Comparison and choice

|     | Transport Layer | Port | Advantages | Bandwidth factor |
| --- |---------------------- |---------------------- | ------------------------------------------------------------------------------------------------------------------------ | ---------------- |
| **[Compact](docs/documentation-msgpack-compact.md)** | `UDP` |default is port `2115` | - smallest traffic <br/> - best fit for PLCs                                                                             | 1                |
| **[MSGPACK](docs/documentation-msgpack-compact.md)** | `UDP` |default is port `2115` | - available libraries in almost all programming languages                                                                | ~2               |
| **[WebSocket](docs/documentation-websocket.md)**     | `TCP` |`80`                   | - uses port `80` which is open in most circumstances <br/> - good for low output frequencies <br/> - uses JSON structure | ~3               |


# Device  configuration - Comparison and choice

|                                          | Transport Layer | Port                   | When to use what                                                                                     |
| ---------------------------------------- | --------------- | ---------------------- | ---------------------------------------------------------------------------------------------------- |
| **[REST](docs/documentation-rest.md)**   | `TCP`           | `80`                   | - if you only want to read data - if your system can handle a challenge and response process         |
| **[CoLa A](docs/documentation-cola.md)** | `TCP`           | default is port `2111` | - if your system cannot handle a challenge and response process <br/>                                |
| **[CoLa B](docs/documentation-cola.md)** | `TCP`           | default is port `2112` | - if your system cannot handle a challenge and response process <br/> - it is the best fit for PLCs. |


# Getting started to work with a sensor

## :zero: Prerequisites 

:heavy_check_mark: SICK sensor (e.g. multiScan100)

:heavy_check_mark: Power cable 

:heavy_check_mark: Ethernet cable to connect the sensor to your system

## :one: See scan data on sensor web server

- Power the sensor
- Connect the sensor to your system. (FAQ: [I can not connect to my sensor? Any ideas?](##I-can-not-connect-to-my-sensor?-AnyIdeas?))
- Open the sensor web browser (default ip address: http://192.168.0.1/)

## :two: Decide how you want to work with the device

- **Case 1**: You want to test the device and change some settings with the given web browser.
  - You are ready to got and do not need any further actions.
- **Case 2**: You want to integrate the device into a ROS environement (ROS / ROS2)
  - Please refer to our [ROS drivers](https://github.com/SICKAG/sick_scan_xd).
- **Case 3**: You want to use an existing driver (C++ or Python)
  - Please refer to our [C++ / Python driver](https://github.com/SICKAG/sick_scan_xd).
- **Case 4**: You want to build your own driver in specidic programming language.
  - Decide which measurement data straming approach you want you use. You can choose from these:
    - Compact Format via `UDP`
    - MSGPACK Format via `UDP`
    - ScanData via `WebSockets`
  - Decide which sensor configuration approach you want you use. You can choose from these:
    - HTTP/REST via `TCP`
    - CoLa via `TCP`


# [FAQ](docs/documentation-faq.md) & [Glossary](docs/documentation-glossary.md)

