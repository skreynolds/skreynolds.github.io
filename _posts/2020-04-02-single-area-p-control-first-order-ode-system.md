---
layout: post
title: "single area p control of a first order ode system"
date: 2020-04-02
---


## the model
To develop a system of first order linear ordinary differential equations for the single area P controlled power system, let $$x_1$$ be the output of the governor; $$x_2$$ be the output from the turbine block; and $$x_3$$ be the output from the generator load demand. This has been labelled on the block diagram shown in Figure 1.

<figure>
	<img src="/assets/single_area_p_control.png" alt="Governor" height="200" class="center">
	<figcaption>Figure 1: TBD</figcaption>
</figure>

The $$x$$ variable assignments can be written as follows:

$$
\begin{align}
	x_1(t) &= \Delta y_E(t) \tag{1} \\
	x_2(t) &= \Delta p_G(t) \tag{2}\\
	x_3(t) &= \Delta f(t) \tag{3}
\end{align}
$$

Now, focusing on the governor block, it is clear that the following equation can be written:

$$\Delta Y_E(s) = [\Delta P_C(s) - \frac{1}{R} \Delta F(s)] \times \bigg( \frac{K_{sg}}{1 + T_{sg}s}\bigg)$$

Rearranging, this can be written as:

$$s\Delta Y_E(s) = \frac{1}{T_{sg}} \big( K_{sg} \Delta P_C(s) - \frac{K_{sg}}{R} \Delta F(s) - \Delta Y_E(s) \big) \tag{4}$$

Similarly, focusing on the turbine block we can write the following expression:

$$\Delta P_G(s) = \bigg( \frac{K_t}{1 + T_t s} \bigg) \times \Delta Y_E(s)$$

Rearranging, this can be written as:

$$s \Delta P_G(s) = \frac{1}{T_t} \big( K_t \Delta Y_E(s) - \Delta P_G(s) \big) \tag{5}$$

Finally, considering the generator-load block, the following expression can be derived:

$$\Delta F(s) = [ \Delta P_G(s) - \Delta P_L(s) ] \times \bigg( \frac{K_{gl}}{1 + T_{gl}s} \bigg)$$

Rearranging, we get the following:

$$s \Delta F(s) = \frac{1}{T_{gl}} \big( K_{gl} \Delta P_t(s) - K_{gl} \Delta P_L (s) - \Delta F(s) \big) \tag{6}$$

Taking the inverse Laplace transform of equations (4), (5), and (6) and yields the following first order system:

$$
\begin{align}
	\frac{d}{dt} \Delta y_E(t) &= \frac{1}{T_{sg}} \big( K_{sg} \Delta p_C(t) - \frac{K_{sg}}{R} \Delta f(t) - \Delta y_E(t) \big) \tag{7} \\
	\frac{d}{dt} \Delta p_G(t) &= \frac{1}{T_t} \big( K_t \Delta y_E(t) - \Delta p_G(t) \big) \tag{8} \\
	\frac{d}{dt} \Delta f(t) &= \frac{1}{T_{gl}} \big( K_{gl} \Delta p_G(t) - K_{gl} \Delta p_L (t) - \Delta f(t) \big) \tag{9} \\
\end{align}
$$ 

Substituting the $$x$$ variable expressions in (1), (2), and (3) allows us to write (7), (8), and (9) a little bit more compactly:

$$
\begin{align}
	\dot{x}_1(t) &= \frac{1}{T_{sg}} \big( K_{sg} \Delta p_C(t) - \frac{K_{sg}}{R} x_3(t) - x_1(t) \big) \tag{10}\\
	\dot{x}_2(t) &= \frac{1}{T_t} \big( K_t x_1(t) - x_2(t) \big) \tag{11} \\
	\dot{x}_3(t) &= \frac{1}{T_{gl}} \big( K_{gl} x_2(t) - K_{gl} \Delta p_L (t) - x_3(t) \big) \tag{12}
\end{align}
$$

## python implementation