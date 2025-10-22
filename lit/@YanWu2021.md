---
title: Design and implementation of OBU terminal for Vehicle Ad-hoc Network
authors: [Yan Wu, Pengkun Wang, Chao Sun]
year: 2021
date: 2025-08-05 12:50
tags: [literature, networking, operating-system]
---

VANET, as stated by the authors, is to connect with everything (V2X). V2V is
understood as the communication between vehicles through **OBU terminal**.

Current on-board system products from stated examples like BYD, Apple, and
General Motor work independently to each other while providing services.

According to the authors' functional analysis, OBU terminal should consist of
security application module and non-security application module. Example
functions of security application module are warning of special vehicle and
fault stop warning. Example functions of non-security application module are
real-time picture, voice message, video call, text transmission, and voice call.

The data storage used was SQLite for non-security applications.

The OBU terminal developed by the authors were deployed on Android system.
