---
layout: post
title: "modelling the governor"
date: 2020-03-09
---

When looking at a single area power system, there are three main components that the literature has a tendency to focus on:

* **Governor**: used for controlling the angular velocity (and frequency) of the system;
* **Turbine**: this is the steam turbine which provides the mechanical torque to drive the generator; and
* **Generator load**: describes the electrical power that is produced and the electrical torque from connected loads. 

The derivations are a bit involved, but worth understanding. This post will cover the basics of how the literature goes about modelling a governor for a steam turbine. Other governor models can be more involved as the mechanical complexity of the turbine increases.

The analysis below will draw heavily from Kothari's awesome book: [*Modern Power Systems Analysis*](https://www.amazon.com.au/Modern-Power-System-Analysis-4e/dp/1259003175/ref=sr_1_1?qid=1586508013&refinements=p_27%3ADr.+D+P+Kothari&s=books&sr=1-1). 

## governor model
The most important part of a speed governor are the two large masses (the pair of balls) which spin around a central axis. These masses are mechanically coupled to the the turbine drive shaft, so their angular velocity is a function of the turbine speed. Elgerd's [*Electric Energy System Theory: An Introduction*](https://www.amazon.com/Electric-Energy-Systems-Theory-Elgerd/dp/007099286X) provides a really great schematic representation of the governing system for a steam turbine, shown in Figure 1. This schematic is used to derive the plant model for the governor. 

<figure>
	<img src="/assets/physical_governor_device.png" alt="Governor" height="400" class="center">
	<figcaption>Figure 1: A schematic of a steam governor</figcaption>
</figure>

If we let $$A$$ on the in the schematic be moved downward a little bit, $$\Delta y_A$$, the turbine power output will change by a directly proportional amount. Letting $$\Delta P_C$$ be the power increase, this can be expressed as:

$$\Delta y_A = k_C \Delta P_C \tag{1}$$

An increase in $$\Delta P_C$$ will cause the pilot valve to move up, and high pressure oil will flow onto the top of the main piston forcing it downwards. As the steam valve opens, more steam will drive the turbine faster and causing the flyball governor to lower point $$B$$. Mathematically, the movement of $$C$$ can be expressed as the result of two separate inputs:

1. Assuming that $$\Delta y_A$$ is small, using similar triangles, it can be written that:

    $$\Delta y_C = - \frac{l_2}{l_1} \Delta y_A$$

2. Given a frequency increase $$\Delta f$$ point $$B$$ will move downward so, assuming $$A$$ is fixed, then using similar triangles it is clear that:

    $$\Delta y_C = \frac{l_1 + l_2}{l_1} \Delta y_B$$

Letting $$k_1 = \frac{l_2}{l_1}$$, $$k_2 = \frac{l_1 + l_2}{l_1} k_2'$$, and using equation (1), the total movement in point $$C$$ can be expressed as:

$$\Delta y_C = - k_1 k_C \Delta P_C + k_2 \Delta f \tag{2}$$

A similar analysis, considering movement of point $$C$$ and $$E$$, can be undertaken to mathematically express the movement of point $$D$$. The analysis also makes use of similar triangles and results in the expression:

$$\Delta y_D = \frac{l_4}{l3 + l_4} \Delta y_C + \frac{l3}{l_3 + l_4} \Delta y_E$$

Letting $$k_3 = \frac{l_4}{l3 + l_4}$$ and $$k_4 = \frac{l3}{l_3 + l_4}$$, this can be re-expressed as:

$$\Delta y_D = k_3 \Delta y_C + k_4 \Delta y_E \tag{3}$$

When there is some movement, $$\Delta y_D$$, of point $$D$$ the ports of the pilot valve will open and high pressure oil will plow onto the cylinder causing some movement $$\Delta y_E$$. If point $$D$$ moves up, high pressure oil will move point $$E$$ down, and conversely if point $$D$$ moves down, high pressure oil will move point $$E$$ upwards. To simplify the dynamics of this scenario, the following assumptions are made:

1. Inertial reaction forces of the main piston and steam valve are negligible compared to the forces exerted on the piston by high pressure oil
2. Due to the first assumption, the rate of oil admitted to to the cylinder is proportional to the port opening $$\Delta y_D$$.

The volume of oil admitted to the cylinder is thus proportional to the time integral of $$\Delta y_D$$. Dividing the oil volume by the cross-sectional area of the piston:

$$\Delta y_E = k_5 \int (- \Delta y_D) dt \tag{4}$$

Taking the Laplace transform of equations (2), (3), and (4) gives the following:

$$
\begin{align}
\Delta Y_C(s) &= -k_1 k_C \Delta P_C(s) + k_2 \Delta F(s)\tag{5} \\
\Delta Y_D(s) &= k_3 \Delta Y_C(s) + k_4 \Delta Y_E(s)\tag{6} \\
\Delta Y_E(s) &= - k_5 \frac{1}{s} \Delta Y_D(s)\tag{7}
\end{align}
$$

Algebraically manipulating (5), (6), and (7) eliminates $$\Delta Y_C(s)$$ and $$\Delta Y_D(s)$$ and results in the following equation:

$$\Delta Y_E(s) = \frac{k_1 k_3 k_C \Delta P_C(s) - k_2 k_3 \Delta F(s)}{k_4 + \frac{s}{k_5}} \tag{8}$$

Equation (8) can be re-expressed as:

$$\Delta Y_E(s) = \bigg[ \Delta P_C(s) - \frac{1}{R} \Delta F(s) \bigg] \times \bigg( \frac{K_{sg}}{1 + T_{sg}s} \bigg) \tag{9}$$

where

$$
\begin{align}
	R &= \frac{k_1 k_C}{k_2} \\
	K_{sg} &= \frac{k_1 k_3 k_C}{k_4} \\
	T_{sg} &= \frac{1}{T_{sg}} 
\end{align}
$$

Equation (9) is the model of the governor in the frequency domain. The parameter $$R$$ is referred to as the speed regulation of the governor; the parameter $$K_{sg}$$ is referred to as the gain of the speed governor; and the parameter $$T_{sg}$$ is referred to as the time constant of the speed governor.

The complete block diagram of governor model can be seen in Figure 2 below.

<figure>
	<img src="/assets/governor_model.png" alt="Governor" height="250" class="center">
	<figcaption>Figure 2: Block diagram of the steam governor model in the frequency domain</figcaption>
</figure>
