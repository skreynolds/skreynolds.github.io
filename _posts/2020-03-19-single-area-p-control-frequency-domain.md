---
layout: post
title: "single area p control in the frequency domain"
date: 2020-03-19
---

A power system is comprised of multiple generators whose output is fed to a transmission network. The transmission network transmits power over great distances, and feeds distribution networks which are the final step in providing invidual consumers and industry with power. The system is comprised of multiple generators and multiple loads.

In order to make things simpler to model, researchers often aggregate generators into a group called a *power area*. Generators are placed into a power area based on characteristics such as geographic location, or the provision of power to a subset of consumers. This simplificaiton is convenient for my purposes because I can use models for a [single governor](https://skreynolds.github.io/blog/2020/03/09/modelling-plant-1), a [single turbine](https://skreynolds.github.io/blog/2020/03/10/modelling-plant-2), and a [single generator load](https://skreynolds.github.io/blog/2020/03/11/modelling-plant-3) to model a single area power system. A block diagram of a single area power system can be seen in Figure 1. This particular model is using a proportional feedback loop to control frequency - the literature refers to this as [primary control](https://skreynolds.github.io/blog/2020/03/12/primary-control).

<figure>
	<img src="/assets/single_area_p_control.png" alt="Governor" height="200" class="center">
	<figcaption>Figure 1: Block diagram of a single area power system using a proportional feedback loop to control frequency</figcaption>
</figure>

MATLAB's Simulink was used to implement this frequency domain model. The program has a handy dandy GUI for drag and drop building of these types of frequency models - the whole thing took me about 10 minutes to make (and fix up all the bugs). The model parameters were selected based on some of the more common values I had come across in these types of classical models. A full break down of the model parameters, including a description and their assigned values, can be seen in Table 1. 

<center>
<table style="width: 75%">
	<caption>Table 1: A summary of the parameters and the values used in the Simulink model</caption>
	<tr><th>Description</th>						<th>Parameter</th>			<th style="text-align: center;">Value</th></tr>
	<tr><td>Speed governor gain</td>				<td>\(K_{sg}\)</td>			<td style="text-align: right;">1.00</td></tr>
	<tr><td>Speed governor time constant</td>		<td>\(T_{sg}\)</td>			<td style="text-align: right;">0.20</td></tr>
	<tr><td>Turbine gain</td>						<td>\(K_{t}\)</td>			<td style="text-align: right;">1.00</td></tr>
	<tr><td>Turbine time constant</td>				<td>\(T_{t}\)</td>			<td style="text-align: right;">0.50</td></tr>
	<tr><td>Generator load gain</td>				<td>\(K_{gl}\)</td>			<td style="text-align: right;">1.25</td></tr>
	<tr><td>Generator load time constant</td>		<td>\(T_{gl}\)</td>			<td style="text-align: right;">12.5</td></tr>
	<tr><td>Speed regulation of the governor</td>	<td>\(R\)</td>				<td style="text-align: right;">0.05</td></tr>
	<tr><td>Load demand change</td>					<td>\(\Delta P_L\)</td>		<td style="text-align: right;">0.02</td></tr>
	<tr><td>Speed changer</td>						<td>\(\Delta P_C\)</td>		<td style="text-align: right;">0.00</td></tr>
</table>
</center>

The completed Simulink implementation of the block diagram is shown in Figure 2. Note that there are a couple of block elements that are not included in Figure 1. The first is the scope --- this is a Simulink element that allows for the recording of simulation signals (it's a bit like an oscilloscope). The second is the out blocks --- these capture data and export it to the MATLAB workspace so you can make pretty plots and stuff.

<figure>
	<img src="/assets/single_area_model_P_control.svg" alt="Governor" height="250" class="center">
	<figcaption>Figure 2: MATLAB Simulink model of the single area power system shown in Figure 1</figcaption>
</figure>

The simulation was run for exactly 11 seconds. The step change in load demand, $$\Delta P_L$$, was set to take place at 1 second after the simulation started --- this is shown in the topmost plot in Figure 3. The frequency response of the system can be seen in the lowermost plot in Figure 3. Note that the controller can arrest the frequency deviation; however, is unable to restore the frequency to the scheduled value. This is consistent with the analysis that was undertaken in the [primary control](https://skreynolds.github.io/blog/2020/03/12/primary-control) post.

<figure>
	<img src="/assets/single_area_p_control_plot.svg" alt="Governor" height="400" class="center">
	<figcaption>Figure 3: The response of the system frequency (below) for a step change in the load demand (above)</figcaption>
</figure>