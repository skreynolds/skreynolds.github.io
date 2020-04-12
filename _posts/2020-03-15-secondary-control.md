---
layout: post
title: "secondary control"
date: 2020-03-15
---

The frequency domain models for the speed [governor](https://skreynolds.github.io/blog/2020/03/09/modelling-plant-1), [turbine](https://skreynolds.github.io/blog/2020/03/10/modelling-plant-2), and [generator load](https://skreynolds.github.io/blog/2020/03/11/modelling-plant-3) can be combined to create a single governor controlled turbine which provides power to a load. This model has a single proportional control feedback loop, which is known in the literature as the [primary control](https://skreynolds.github.io/blog/2020/03/12/primary-control) loop. If the speed changer signal $$\Delta P_C$$ is set to zero and the governor is allowed to operate under *free governor operation*, then for a step change in the load demand, $$\Delta P_L$$, the primary controller will be able to arrest frequency deviations; however, will not be able to return the system frequency to the schedled value. This is not really a desirable property in a controller - we need to do something else.

Motivated by the fact that the system frequecy can be returned to the scheduled value using the governor speed changer, we add an additional feedback control loop to the system. The additional control loop using an integral controller, with gain parameter $$K_i$$. This additional feedback loop is referred to as the secondary control in the literature. The primary and secondary controllers together form what is commonly know as a proportional integral (PI) controller. The updated block diagram of the system is shown in Figure 1.

<figure>
	<img src="/assets/single_area_pi_control.png" alt="Governor" height="200" class="center">
	<figcaption>Figure 1: Block diagram of proportional integral controller for a single governor controlled generator supplying a single load</figcaption>
</figure>

Note that there is now only a single input to the system, the load demand $$\Delta P_L$$. The step change for the load demand, in the frequency domain, can be expressed as:

$$\Delta P_L(s) = \frac{\Delta P_L}{s} \tag{1}$$

Using algebra, and playing a whole lot of banjo music (or the Benny Hill theme song), the transfer function for the system in Figure 1 can be expressed as:

$$\frac{Delta F(s)}{\Delta P_L (s)} = \frac{}{}$$