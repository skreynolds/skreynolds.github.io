---
layout: post
title: "single area pi control in the frequency domain"
date: 2020-03-21
---

My previous [post](https://skreynolds.github.io/blog/2020/03/19/single-area-p-control-frequency-domain) saw the successful implementation of a single area power system simulation in MATLAB's Simulink. This model used a proportional (P) feedback loop for controlling the system frequency when faced with a step change to load demand. As detailed in my post on [primary controllers](https://skreynolds.github.io/blog/2020/03/12/primary-control), this type of control is not able to restore the system frequency to the scheduled value - the simulation confirmed this analysis. 

This post will be almost identical, except for the fact that an additional feedback loop will be added to the model. I have previously written about [secondary control loops](https://skreynolds.github.io/blog/2020/03/15/secondary-control) - this type of controller sees an integral feedback loop connected to the speed changer input $$\Delta P_C$$. The block diagram can be seen in Figure 1 below.

<figure>
	<img src="/assets/single_area_pi_control.png" alt="Governor" height="200" class="center">
	<figcaption>Figure 1: </figcaption>
</figure>

MATLAB's Simulink was used to implement this frequency domain model. The model parameter values are almost identical to the ones used in the previous post, which were selected from some of the more common values I have seen in the literature. A full breakdown of the model parameters, including a description and their assigned values, can be seen in Table 1. 

<center>
<table style="width: 75%">
	<caption>Table 1: A summary of the parameters and the values used in the Simulink model</caption>
	<tr><th>Description</th>					<th>Parameter</th>			<th style="text-align: center;">Value</th></tr>
	<tr><td>Speed governor gain</td>			<td>\(K_{sg}\)</td>			<td style="text-align: right;">1.00</td></tr>
	<tr><td>Speed governor time constant</td>	<td>\(T_{sg}\)</td>			<td style="text-align: right;">0.20</td></tr>
	<tr><td>Turbine gain</td>					<td>\(K_{t}\)</td>			<td style="text-align: right;">1.00</td></tr>
	<tr><td>Turbine time constant</td>			<td>\(T_{t}\)</td>			<td style="text-align: right;">0.50</td></tr>
	<tr><td>Generator load gain</td>			<td>\(K_{gl}\)</td>			<td style="text-align: right;">2.00</td></tr>
	<tr><td>Generator load time constant</td>	<td>\(T_{gl}\)</td>			<td style="text-align: right;">20.00</td></tr>
	<tr><td>Load demand change</td>				<td>\(\Delta P_L\)</td>		<td style="text-align: right;">0.02</td></tr>
	<tr><td>Speed changer</td>					<td>\(\Delta P_C\)</td>		<td style="text-align: right;">0.00</td></tr>
</table>
</center>

The completed Simulink implementation of the block diagram is shown in Figure 2. As with the previous post, there are a couple of additional block elements that are not shown in Figure 1 --- these are described in full in my [previous post](https://skreynolds.github.io/blog/2020/03/19/single-area-p-control-frequency-domain).

<figure>
	<img src="/assets/single_area_model_PI_control.svg" alt="Governor" height="300" class="center">
	<figcaption>Figure 2: MATLAB Simulink model of the single area power system shown in Figure 1</figcaption>
</figure>

The simulation was again run for exactly 11 seconds. The step change in the load demand, $$\Delta P_L$$, was again set to take place at 1 second after the simulation started --- shown in the topmost plot in Figure 3. The frequency response can be seen in the lowermost plot in Figure 3. This result shows an improvement of the PI controller over a P controller. Notably, the PI controller is able to restore the power system to it's scheduled operation frequency.

<figure>
	<img src="/assets/single_area_pi_control_plot.svg" alt="Governor" height="400" class="center">
	<figcaption>Figure 3: The response of the system frequency (below) for a step change in the load demand (above)</figcaption>
</figure>

