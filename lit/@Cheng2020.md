---
title: An Improved RSU-based Authentication Scheme for VANET
authors: [Hongyuan Cheng, Yining Liu]
year: 2020
date: 2025-08-23 18:08
tags: [literature, networking, security, authentication, transporation]
---

The authors stated that a typical model of a classic VANET architecture consists
of onboard unit (OBU), Trust Authority (TA), and roadside unit (RSU).

TA is a fully trusted third party that is responsible for generating system
parameters and registration of vehicles and RSUs. It is also responsible for
tracking the true identity of malicious vehicle in security sense.

RSU is a fixed-position entity that has large storage capacity and powerful
communication capability. It is responsible for generating pseudonym and private
key for vehicles. RSU also equips with tamper-proof device (TPD) for storing
system master key of TA.

The pseudonym is useful for TA to track down vehicles in the network.

The main goal of VANET is to improve road safety and driving conditions by
sharing information among vehicles. Primarily, there are two communication
models in VANET, i.e., V2V and V2I.

DSRC provides a communication range from 100 to 1000 metre. Vehicle broadcast
messages every 100 to 300 ms.

The opennesses of VANET communication, claimed by the authors, cause concern in
security and privacy. The network is exposed under possible attack of
[impersonation attack](../202209262114.md) and [Replay Attack](../202209262121.md).
The latter can be done by [intercepting](../202209261916.md) the messages on
public channel. It is possible in VANET, if no mechanism to counter, to track
vehicle's route through its identity due to expose privacy.

The authors listed the security and privacy requirements for VANET, which
include **mutual [Authentication](../202210040915.md), message
[authentication](../202210022151.md) and [Integrity](../202210022154.md),
identity privacy, traceability, [Non-Repudiation](../202210022159.md),
unlinkability, and resistance to [Attack](../202209261358.md).**

**Mutual authentication** means that vehicle and RSU have to prove their identity to
each other before performing communication related function.

**Identity privacy** concerns about keeping the real identity from other
vehicles and RSUs.

**Traceability** is related to pseudonym, which has been explained before, that
is, used by TA to track the real identity of a vehicle, especially the malicious
adversaries.

**Unlinkability** is a requirement that tries to make linking 2 or more than two
received messages impossible. This would conceive the real identity of the
vehicle if those messages are sent by the same vehicle.

**Resistance to attack** deals with impersonation attack, replay attack, and
[Modification](../202209261922.md) attack.
