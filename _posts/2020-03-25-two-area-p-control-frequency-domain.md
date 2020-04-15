---
layout: post
title: "two area p control in the frequency domain"
date: 2020-03-25
---

<figure>
	<img src="/assets/two_area_control_block.png" alt="Governor" height="400" class="center">
	<figcaption>Figure 1: Block diagram of a single area power system using a proportional feedback loop to control frequency</figcaption>
</figure>

<center>
<table style="width: 75%">
	<caption>Table 1: A summary of the parameters and the values used in the Simulink model</caption>
	<tr><th>Description</th>						<th>Parameter</th>								<th style="text-align: center;">Value</th></tr>
	<tr><td>Speed governor gain</td>				<td>\(K_{sg1}, K_{sg2}\)</td>						<td style="text-align: right;">1.00</td></tr>
	<tr><td>Speed governor time constant</td>		<td>\(T_{sg1}, T_{sg2}\)</td>						<td style="text-align: right;">0.20</td></tr>
	<tr><td>Turbine gain</td>						<td>\(K_{t1}, K_{t2}\)</td>						<td style="text-align: right;">1.00</td></tr>
	<tr><td>Turbine time constant</td>				<td>\(T_{t1}, T_{t2}\)</td>						<td style="text-align: right;">0.50</td></tr>
	<tr><td>Generator load gain</td>				<td>\(K_{gl1}, K_{gl2}\)</td>						<td style="text-align: right;">1.25</td></tr>
	<tr><td>Generator load time constant</td>		<td>\(T_{gl1}, T_{gl2}\)</td>						<td style="text-align: right;">12.5</td></tr>
	<tr><td>Speed regulation of the governor</td>	<td>\(R_1, R_2\)</td>							<td style="text-align: right;">0.05</td></tr>
	<tr><td>Load demand change</td>					<td>\(\Delta P_{L1}, \Delta P_{L2}\)</td>		<td style="text-align: right;">0.02</td></tr>
	<tr><td>Speed changer</td>						<td>\(\Delta P_{C1}, \Delta P_{C2}\)</td>		<td style="text-align: right;">0.00</td></tr>
	<tr></tr>
</table>
</center>

<figure>
	<img src="/assets/two_area_model_P_control.svg" alt="Governor" width="100%" class="center">
	<figcaption>Figure 2: MATLAB Simulink model of the single area power system shown in Figure 1</figcaption>
</figure>

<figure>
	<img src="/assets/two_area_p_control_plot.svg" alt="Governor" height="400" class="center">
	<figcaption>Figure 3: The response of the system frequency (below) for a step change in the load demand (above)</figcaption>
</figure>