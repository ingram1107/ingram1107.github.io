---
title: Vehicular Ad-hoc Network (VANET) - A Review
authors: [Ahmed Ghassan Hameed, Mahmoud Shuker Mahmoud]
year: 2022
date: 2025-07-23 14:09
tags: [literature, networking, iot, transporation, security]
---

# Introduction

This paper provides an overview on VANET's architecture, characteristics,
security, [Routing Protocol](../202207061815.md), applications, simulators, and
5G integration.

The authors defined **ad-hoc network** is a network where devices can directly
communicate with each other, using spontaneous establishment of network. This
means they often evade access point like a router.

[Mobile Ad-Hoc Network (MANET)](../202304151351.md) is an infrastructureless,
dynamic, and self-configuring network with free moving nodes.

FANET is a type of MANET that involves UAVs.

VANET can be seen as a type of MANET with a set of mobile (vehicles) and fixed
(roadside units) entities that share information such as road conditions and
other vehicles. Compare to MANET, it has high node mobility, high node density,
fast topology change, and high computational power. VANET uses regular mobility
model, close to ground radio propagation model (where LoS is not available),
localisation technologies such as GPS, AGPS (Assisted GPS), and DGPS
(Differential GPS). Unlike MANET, concerns about power consumption and network
lifetime can be ignored.

The authors stated that the main objective of VANET is to offer safety and
security for the road users by aggregating accidents or uncertain conditions and
traffic data. There are several communication ways: V2V, V2S, V2I, I2I
(intra-infrastructure), V2PD (PD as in personal device), and V2CN (CN as in
cellular infrastructure).

# Architecture

**Note**: RSU is road-side unit.

**Note**: OBU is on board unit.

US Federal Communication Commission (FCC) allocated 75 MHz spectrum at 5.9 GHz
to V2V communication, in addition of IEEE's Dedicated Short Range Communication
(DSRC) technology. In V2I, LTE-A is mostly employed to alert potential road
hazards. In I2I, RSUs communicate with each other through wired or wireless
medium.

DSRC is designed to ensure reliability of safety applications, considering the
time constraint for this type of application. Its primary model is IEEE 802.11p
which provides specification for wireless MAC and physical layers for wireless
access in vehicular environments (WAVE).

In VANET, vehicles use OBU to exchange information with other OBU and RSU. They
also install a set of wireless sensors. RSU is equipped with network devices,
which extend the communication range by relaying, run safety applications such
as traffic condition report and accident warning, and provide Internet
connectivity. Data rate in I2I is constant regardless of network topology or
distance, while in V2V or V2I this varies as a function of network topology and
node distance.

# Characteristics

VANET is *more expensive* than MANET due to rich set of sensors and
communication devices like processors, memory, and communication antennas. It
primarily uses short-distance communication when vehicles are close to each
other while demotes long-range signals to communicate with RSU. Life distance of
vehicle link is short due to movement of vehicles and thus results in **dynamic
topology** (topology almost changes) which cause severe application latency and
bandwidth requirement.

VANET also needs to handle more security than other wireless network due to
dynamic topology. Due to high mobility and dynamic topology, **frequent
disconnections of nodes** is an issue. One good side of VANET is that power
constraint is not a problem since **long-life batteries** provide constant power
to OBUs.

VANET is associated with limited bandwidth (75 MHz), which has a maximum
theoretical [Throughput](../202304111957.md) of 27 Mbps.

# Security

As stated before, the authors wrote that security concerns are demanding in
VANET due to node's high mobility which causes regular infrastructure changes
and requires quicker path and route updates. V2I links are less vulnerable to
attacks while comparing to V2V, but they require more bandwidth.

The authors concluded that the conditions to keep VANET to properly carry out
network operation includes: [Availability](../202210022157.md),
[Access Control](../202210022203.md), [Integrity](../202210022154.md),
[Confidentiality](../202210022150.md), [Authentication](../202210022151.md), and
[Non-Repudiation](../202210022159.md).

**Note**: Authentication in VANET, as stated by the authors, should ensure that
all nodes are authenticated before launching services. Authentication is used
when a node needs service or wishes to join the network.

VANET attack types were categorised by the authors according to architecture,
which are on **wireless interface**, **hardware and software**, **sensors input
in vehicle**, and **infrastructure**.

Examples of security attacks on wireless interface include
[DoS](../202209262115.md), DDoS, Sybil, [Malware](../202301031611.md) and spam,
brute force, [Man-In-The-Middle Attack (MITM)](../202210132201.md), location
tracking, tunnelling, blackhole, and grayhole.

Examples of security attacks on hardware and software are DoS, Sybil, malware
and spam, brute force, MITM, spoofing and forgery, cheating with position
information or GPS spoofing, message suppression or alteration, fabrication
replay, [Masquerade](../202209262114.md), injection of erroneous message or
bogus information, tampering hardware, routing, blackhole, wormhole, grayhole,
and timing.

Examples of security attacks on sensors input in vehicle include GPS spoofing,
illusion attack, and jamming.

Examples of security attacks on infrastructure are DoS, DDoS, spoofing,
impersonation, masquerade, session hijacking, unauthorised access, tampering
hardware, and repudiation.

At the time of the authors' research (2022), there is no sufficient way to
secure VANET applications. Hussain et al. in their paper (published in 2019)
"Integration of VANET and 5G Security: A review of deign and implementation
issues" suggested the integration with 5G technology to handle security in the
upper layer ([Application Layer](../202206131856.md) and [Network Layer](../202206131702.md))
and lower layer ([Physical Layer](../202206131647.md)). Such integration will
be elaborated further in the following discussions.

In the 2019 paper "Trust Evaluation Framework in Vehicular Ad-Hoc Networks",
Ahmed proposed Trust Evaluation and Management (TEM) framework, built using
VEINS, which incorporates SUMO mobility simulator and OMNETH network simulator.
Ahmed claimed TEM is effective in simulating a wide range of Trust Models (TMs)
where efficiency is checked with multiple [QoS](../202209282057.md) and
security related criteria.

# Routing Protocol

The authors categorised [Routing Protocols](../202207061815.md) in VANET into
five: *topology-based*, *position-based*, *cluster-based*, *multicast-based*,
and *broadcast-based*.

Topology-based routing protocols use [Shortest-Path Algorithm](../202204141149.md)
and is both suitable for small VANET if used in proactive mode and large size of
mobile VANET in reactive mode. Reactive mode has a clear advantage to proactive
counterpart is that there is no need to update [Routing Table](../202210112056.md).
Examples of this type of routing protocol are *Destination Sequence Distance
Vector Routing (DSDV, proactive)*, *Ad Hoc On-Demand Distance Vector (AODV,
reactive)*, and *Zone Routing Protocol (ZRP, hybrid)*.

Position-based routing protocols are suited for high mobility scenario. With
this kind of protocols, there is no need for route discovery, maintenance, and
topology knowledge. However, they require online working of GPS devices. Example
of such protocols including *Motion Vector Routing Algorithm (MOVE)*.

Cluster-based routing protocols divide VANET into clusters, and vehicles are
connected directly inside their cluster. The cluster head manages the connection
between clusters. This is suited for large VANET, though they suffer from
overhead and delays in highly dynamic network. Example of these protocols is
*Clustering for Open Ivc Network (COIN)*.

Broadcast-based routing protocols send data to all nodes inside the broadcast
domain and can be used for route discovery. Compare to other kind of routing
protocols, they can facilitate reliable data transmission, but require high
network bandwidth. Example of them is *Density-Aware Reliable Broadcasting
(DECA)*.

Multicast-based routing protocols divide VANET into zones located in a specific
geographical area and use multicast position-based routing. They are reliable in
highly dynamic topology. However, they suffer from transmission delay caused by
network disconnection. Example from them is *Robust Vehicular Routing (ROVER)*.

# Application

The applications can be categorised into safety and non-safety, as stated by
Hameed et al.

Safety VANET applications can further be subcategorised into *sensing-based
applications* and *traffic efficiency applications*. The former depends on
devices embedded in OBU like safety sensors, GPS, camera, and distance sensors.
Examples of such application include Active Safety Application (ASA), Passive
Safety Application (PSA), Post-Crash Warning (PCW), Warning Application (WA),
and Lane Change Assistance Warning (LCAW). Traffic efficiency applications, on
the other hand, aim to enhance vehicular traffic efficiency based on
collaboration between vehicles. Examples of those include Intersection Collision
Warnings (ICW), Cooperative Forward Collision Warnings (CFCW), and Pedestrian
Crossing Safety Warnings (PCSW).

Non-safety VANET applications provide enjoyable and convenient services such as
information on weather, gas stations, hotels, parking lots, shopping malls,
restaurants etc.

Safety-related applications require minimum delay and latency and secure against
attacks. Non-safety applications, in contrast, doesn't need such strict
requirements, but they can be bandwidth-demanding.

# Simulator

VANET simulators can be categorised into network simulator (NS), mobility
simulator (MS), and integrated simulator (IS).

NS simulates data packets in OSI layers and deals with communications. MS
generates node movements based on map road, where the researchers recommended
the use of Open Street Map. The identification of new route is achieved with the
combination of GPS and vehicle based software like Radio Data System-Traffic
Message Channel (RDS-TMC). IS performs both features of NS and MS, and often
done it by combining both NS and MS.

The recommended NS are NS3 and OMNET++. For MS, it's SOMO. As for IS, there are
TraNS and VEINS.

# Integration with 5G

VANET relies on DSRC and WAVE technology while supports [Cellular Network](../202303292214.md),
[WiFi](../202303292155.md), and [WiMAX](../202305181312.md). DSRC and WAVE
provides limited bandwidth and transmission range while suffer from high latency
and low security. To solve the bandwidth issue and short transmission range, the
deployment of 3G and 4G is necessary. For the latter problems, 5G is recommended
as it provides 10 Gbps and 1 ms latency. Another advantage of deploying 5G in
VANET is its unique feature of network slicing, which enables 5G to establish
multiple virtual network connections based on the type of requested service.
