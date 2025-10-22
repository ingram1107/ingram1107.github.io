---
title: Timestamp Based Detection of Sybil Attack in VANET
authors: [Syed Mohd Faisal, Taskeen Zaidi]
year: 2020
date: 2025-07-31 14:41
tags: [literature, networking, security, transporation]
---

# Introduction

VANET is a subset of MANET. While MANET works with slow standby unit, VANET
works with shift moving nodes.

VANET has the characteristics of *high node mobility, high node density,
frequent changes in network topology, low energy constraints, moving pattern
nodes constrained by road, communication range up to 500 m (MANET's 100 m),
medium to high node speed (20 to 100 km/hour compare to MANET's 6 km/hour), high
scalability, thousands Kbps bandwidth, and high [QoS](../202209282057.md).*

VANET is to be used to enforce **Intelligent Transport System (ITS)** based on
IEEE 802.11p for WAVE.

There are two primary communication ways in VANET, i.e., V2V and V2I. For V2V,
there is no need of infrastructure support as it creates self-network that can
range up to 500 meter. The communication is done using OBU (on-board unit). V2V
shares message on safety messages, vehicle identities, information on malicious
vehicle etc. On the other hand, V2I needs RSU (road-side unit) to exchange
information on road conditions, nearby services like hotel and gas station, and
provide internet access. The following picture shows the VANET infrastructure.

![VANET Architecture](../pic/vanet-arch.png)

From the above illustration, we can see that RSU is connected to the Internet,
Certificate Authority, and ITS services.

# Security Concerns and Sybil Attack

VANET inherits wireless network security threats. Due to its high intensity of
connection and discovery of vehicle, network topology changes frequently. Such
frequent change of topology result in great chance of attack at the time of
handoff.

As such, to ensure security, the authors stated that VANET has to take care
about [authentication](../202210022151.md), [Integrity](../202210022154.md),
[Availability](../202210022157.md), [Confidentiality](../202210022150.md),
[Non-Repudiation](../202210022159.md), privacy, and scalability.

**Note**: The authors gave the examples of confidential information in VANET:
session key, payment data, and OTP.

Sybil attack is first introduced by Douceur. It is an attack on the network
itself. This is done through a malicious vehicle impersonating multiple
legitimate identities by forging new identity or steal them from vehicles of the
network. Such stealing is done by eavesdropping broadcasting messages which were
intended to update routing table. Sybil attack creates an illusion of presence
of multiple legitimate vehicles in the network. It has the potential to
influence the functioning of VANET services such as update routing tables,
voting, fair resource allocation, misbehaviour detection, data aggregation etc.
The attacker can take control over the network, which then they may inflict
other attacks like black hole attack, timing attack,
[DoS](../202209262115.md), impersonation attack etc.

Since VANET has no logical central authority, many protocols award unique
identity to vehicles which then apply security rules and measures to defend from
Sybil attack.

# Current Defensive Mechanisms

As organised by the authors, there are 6 directions on constructing a defence
mechanism against Sybil attack. They are *resource testing method, position
verification method, domain specific, trusted devices, trusted certification
method, and neighbour list method.*

**Resource Testing Method** tests vehicle resource, that is, radio resource,
memory resource, identification resource, and computational resource. It assumes
every vehicle has the same and limited computational resources, and based on
this assumption, it distributes a puzzle in the network to check vehicle's
computational ability. Since Sybil node has multiple identities at the same
time, it is said to be impossible for the attack to perform additional
computational task, thus failing the test. However, this assumption is flaw as
Sybil node can be equipped with more computational resources to avoid detection.
As such, resource testing method is not sufficient in detecting and preventing
Sybil attacks, as it is restricted to identifying false identities.

**Position Verification** assume that a vehicle can only present on one position
at a time. With this defensive mechanism, the physical location of the vehicle
is verified before data transmission. The network will request all bound
vehicles to respond with their position coordinates. If multiple nodes exhibit
the same geographical coordinates, they are identified as a Sybil node and
action will be taken to eliminate it. This come with downside of requiring extra
hardware, and there is no such guarantee that all vehicles are legitimate. The
attacker may change the geographical coordinates and forward it, and there is no
mechanism to identify and track the actual geographical coordinates.

**Domain Specific** detects Sybil node based on location or geographical
position of the vehicles. If an attacker vehicle having single device and starts
performing Sybil attack, all Sybil vehicles will move together in unison with
same speed in specific domain. The network will track the trajectory and pattern
of the Sybil vehicles and generate alert signal. In the case when the attacker
uses multiple devices, this method is not sufficient. Though the authors said
that this is a better technique for detection while admitted it is restricted
and can generate falsie result when vehicle creates its replica.

**Trusted Devices** are combined with *trusted certification* where the binding of
hardware with vehicles restrict them on obtaining multiple false keys. This
defence mechanism is sufficient to secure the network from Sybil attack, but it
requires extra hardware. That being said, there is no efficient mechanism to
restrict vehicle from obtaining multiple trusted devices without manual
interaction. Compare to trusted certification, since there is no central
authority, vehicle can equip with multiple trusted devices in which this method
will fail to detect.

**Trusted Certification** is currently the most common solution as stated by the
authors, due to the ease of implementation and potential to remove Sybil from
the network. There are two entities that are responsible in vehicle
identification in this schema: *third-party certification authority* and
*centralised authority*. Third-party certification authority issues identities
whereas centralised authority assigns them. Centralised authority also has to
ensure the uniqueness of the certificate, and issuing unique identity to a
vehicle has to be done manual as there is no such mechanism for it. Due to this
issue, this will create a bottleneck in large scale system. Regardless, this
method doesn't need additional hardware. Another issue is the database
management on used, unused, lost, and stolen identities. Trusted certification
comes with the downside of requiring huge among of data transmission for
identity validation and blind reliance on third-party certificate. If the attack
is made on the centralised authority, it will bring down the whole system and
consequently gain full privilege of the network. Additionally, there is no
proper mechanism to identify lost and stolen certification, thus identification
of false certificate requires a good amount of computation power and time.

**Neighbour List** utilises a list of neighbour vehicle. It assumes if a vehicle
is observing the same neighbour vehicles simultaneously for a long duration of
time, then there must be a Sybil node in the network. This scheme is complex as
after each time interval, vehicles share a list of neighbour vehicle to detect
Sybil node. An intersection operation is performed on the list generated at
different intervals, and then mark suspected vehicles (neighbour vehicle for
seamlessly long duration). This method puts extra overload by sharing list of
neighbour vehicles, thus requiring computation power and time. When the
computation has been done, the attacker may have completed their attack and
left. At the same time, it still fails to detect Sybil node in some cases like
when Sybil vehicle refuse to share the list or when it claims not to be a
neighbour of any.
