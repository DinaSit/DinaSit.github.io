---
title: Proxy for split traffic routing
date: 2026-07-23
links:
  - type: site
    url: https://github.com/DinaSit/vpn-bypass-proxy
tags:
  - C++
  - Networking
  - macOS
---

A local HTTP/HTTPS proxy for macOS that splits browser traffic between
different routes.

<!--more-->

The program accepts connections from the browser and decides which path each
request should take. It works at the level of network protocols and operating
system interfaces.

The project gave practice in what is usually hidden behind ready-made libraries
in coursework: parsing headers, establishing a tunnel with the `CONNECT`
method, and handling concurrent connections.
