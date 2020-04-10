---
layout: post
title: "modelling the governor"
date: 2020-03-09
---

When considering a single area power system, there are three main components that the literature focuses on:

* **Governor**: used for controlling the angular velocity (and frequency) of the system;
* **Turbine**: which provides the mechanical torque to drive the generator; and
* **Generator and electrical load**: desciribes the electrical power that is produced and the electrical torque from connected loads. 

This post will cover the basics of how the literature models the governor, and will draw heavily from Kothari's awesome book: *Modern Power Systems Analysis*. 

## Governor Model
The main component of a speed governor consists of two large masses which spin around a central axis, driven angular rotation of the turbine drive shaft. The image below, taken from Wikipedia, shows an example of this. 

<img src="/assets/ashton_frost_engine_governor" alt="Ashton Frost Engine Governor" height="300" class="center">

Elgerd's *Electric Energy System Theory: An Introduction* provides a schematic representation of the governing system of steam turbine, shown below. This schematic can be used as a starting point to derive the plant model. 

<img src="/assets/physical_governor_device.png" alt="Governor" height="300" class="center">

Assuming that the system is operating at some steady state, we can say that the linkage mechanisms are static, and the pilot valve is closed. We note that the steam valve is open at some definite value, and the turbine is running at a constant speed. Under these conditions we define the following operating conditions:

* $$ f_0 $$ = system frequency (speed)
* $$ ( P_G )_0 $$ = generator output = turbine output (neglecting generator losses)
* $$ ( y_E )_0 $$ = steam valve setting

If we let $$A$$ on the in the schematic be moved downward a little bit, $$\Delta y_A$$, the turbine power output will change by a directly proportional amount. Letting $$\Delta P_C$$ be the power increase, this can be expressed as:

$$\Delta y_A = k_C \Delta P_C \tag{1}$$

An increase in $$\Delta P_C$$ will cause the pilot valve to move up, and high pressure oil will flow onto the top of the main piston forcing it downwards. As the steam valve opens, more steam will drive the turbine faster and causing the flyball governor to lower point $$B$$. Mathematically, the movement of $$C$$ can be expressed as the result of two separate inputs:

1. Assuming that $$\Delta y_A$$ is small, using similar triangles, it can be written that:
$$\Delta y_C = - \frac{l_2}{l_1} \Delta y_A$$

2. Given a frequency increase $$\Delta f$$ point $$B$$ will move downward so, assuming $$A$$ is fixed, then using similar triangles it is clear that:
$$\Delta y_C = \frac{l_1 + l_2}{l_1} \Delta y_B$$

Letting $$k_1 = \frac{l_2}{l_1}$$, $$k_2 = \frac{l_1 + l_2}{l_1} k_2'$$, and using equation XXXX, the total movement in point $$C$$ can be expressed as:
$$\Delta y_C = - k_1 k_C \Delta P_C + k_2 \Delta f$$

A similar analysis, considering movement of point $$C$$ and $$E$$, can be undertaken to mathematically express the movement of point $$D$$. The analysis also makes use of similar triangles and results in the expression:
$$\Delta y_D = \frac{l_4}{l3 + l_4} \Delta y_C + \frac{l3}{l_3 + l_4} \Delta y_E$$

Letting $$$$ and $$$$, this can be re-expressed as:
$$\Delta y_D = \frac{l_4}{l3 + l_4} \Delta y_C + \frac{l3}{l_3 + l_4} \Delta y_E$$