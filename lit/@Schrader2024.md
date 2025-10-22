---
title: Calibrating Car-Follwoing Models Using SUMO-in-the-Loop and Vehicle
Trajectories From Roadside Radar
authors: [Maxwell Schrader, Arya Karnik, Alexander Hainen, Jashua Bittle]
year: 2024
date: 2025-08-26 09:36
tags: [literature, networking, tranportation]
---

The paper focused on Kruass, Intelligent Drive Model (IDM), and W99 Car
Following Models.

IDM is widely used, including SUMO.

Krauss model is the default car following model in SUMO. It ensures
collision-free travel by calculating the safe speed, $v_{\text{save}}(t)$,
for each following vehicle at very simulation step. The formula is shown as
below:

$$
v_{\text{safe}}(t) = v_l + \frac{g(t) - v_l (t) \cdot \tau}{\frac{v_f}{b \cdot v_f} + \tau}
$$

**Notations**:
- $g(t)$ is the gap to the leading vehicle
- $\tau$ is the reaction time
- $b$ is the comfortable breaking acceleration.

The desired speed, $v_{\text{des}}(t)$ is factored in the vehicle's maximum
acceleration and the driver's behaviour. The calculation is shown as follows:

$$
v_{\text{des}}(t) = \text{min}[v_{\text{safe}}(t), v_f(t) + a, v_0]
$$

**Notations**:
- $a$ characterises the driver's preferred maximum acceleration
- $b$ characterises the driver's preferred maximum deceleration

The results from the paper showed that default settings for IDM and Krauss tend
to favour shorter time headways. The default parameters of Krauss resulted in
762 collisions, far larger than W99's 81 and IDM's 3.
