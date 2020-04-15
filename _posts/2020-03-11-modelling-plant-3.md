---
layout: post
title: "modelling the generator load"
date: 2020-03-11
---

When looking at a single area power system, there are three main components that the literature has a tendency to focus on:

* **Governor**: used for controlling the angular velocity (and frequency) of the system;
* **Turbine**: this is the steam turbine which provides the mechanical torque to drive the generator; and
* **Generator load**: describes the electrical power that is produced and the electrical torque from connected loads. 

The derivations are a bit involved, but worth understanding. This post will cover the basics of how the literature goes about modelling a the generator load of a power system.

The analysis below will draw heavily from Kothari's awesome book: [*Modern Power Systems Analysis*](https://www.amazon.com.au/Modern-Power-System-Analysis-4e/dp/1259003175/ref=sr_1_1?qid=1586508013&refinements=p_27%3ADr.+D+P+Kothari&s=books&sr=1-1).

## generator load model
If the turbine output is in some steady state, and the power system experiences some perturbation, then let the incremental power from the turbine be $$\Delta P_G$$. Noting that the main perturbation experienced by a power system is the change in load demand, $$\Delta P_L$$, the incremental input to the generator-load system is given by $$\Delta P_G - \Delta P_L$$.

The increment in power input to the system is accounted for in two ways:

1. Rate of increase of stored kinetic energy in the generator rotor. At scheduled frequency $$f_0$$, the stored energy is:

    $$(W_{ke})_0 = H \times P_r$$

    where $$P_r$$ is the kilowatt rating of the turbo-generator and $$H$$ is defined as it's inertial constant. Given that the kinetic energy is proportional to the square of the speed (frequency), the kinetic energy at a frequency of $$f_0 + \Delta f$$ can be written as:

    $$W_{ke} = (W_{ke})_0 \bigg( \frac{f_0 + \Delta f}{f_0} \bigg)^2 \approx H P_r \bigg( 1 + \frac{2\Delta f}{f_0} \bigg) $$

    The rate of change of kinetic energy is therefore:

    $$\frac{d}{dt}(W_{ke}) = \frac{2 H P_r}{f_0} \frac{d}{dt} (\Delta f) \tag{1}$$

2. Given that motors make up a reasonable percentage of the load demand it must be considered that the motor load changes as the frequency changes. The rate of change of load with respect to frequency, $$\frac{\partial P_L}{\partial f}$$, can be considered constant for small changes in frequency $$\Delta f$$ and can be expressed as:

    $$\frac{\partial P_L}{\partial f} \Delta f = B \Delta f \tag{2}$$

    where $$B$$ can be empirically determined, and is dependent on the proportion of motors that comprise the load demand. Note that is $$B$$ is positive, then the the load is predominantly comprised of motors.

Using equations (1) and (2), the power balance equation for the incremental input to the generator-load system can be written as:

$$\Delta P_G - \Delta P_L = \frac{2 H P_r}{f_0} \frac{d}{dt} (\Delta f) + B \Delta f$$

Dividing throughout by $$P_r$$ yields the following:

$$\Delta P_G(pu) - \Delta P_L(pu) = \frac{2 H}{f_0} \frac{d}{dt} (\Delta f) + B(pu) \Delta f \tag{3}$$

Taking the Laplace transform of equation (3) and rearranging, we get the following expression:

$$\Delta F(s) = \frac{\Delta P_G(s) - \Delta P_L(s)}{B + \frac{2H}{f_0}s} \tag{4}$$

Equation (4) can re-expressed as:

$$\Delta F(s) = [\Delta P_G(s) - \Delta P_L(s)] \times \bigg( \frac{K_{gl}}{1 + T_{gl}} \bigg) \tag{5}$$

where

$$
\begin{align}
K_{gl} &= \frac{1}{B} \\
T_{gl} &= \frac{2H}{B f_0}
\end{align}
$$

Equation (5) is the model of the generator-load in the frequency domain. The parameter $$K_{gl}$$ is referred to as the gain of the generator load; and the parameter $$T_{gl}$$ is referred to as the time constant of the generator load.

The complete block diagram of governor model can be seen in Figure 2 below.

<figure>
	<img src="/assets/generator_load_model.png" alt="Governor" width="75%" class="center">
	<figcaption>Figure 2: Block diagram of the generator load model in the frequency domain</figcaption>
</figure>