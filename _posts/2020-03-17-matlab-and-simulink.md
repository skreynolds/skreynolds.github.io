---
layout: post
title: "matlab and simulink"
date: 2020-03-17
---

At this point in my research, I have found a couple of models for a single governor controlled generator powering a single load. With the help of [Kothari](https://www.amazon.com.au/Modern-Power-System-Analysis-4e/dp/1259003175/ref=sr_1_1?qid=1586508013&refinements=p_27%3ADr.+D+P+Kothari&s=books&sr=1-1) and [Kundar](https://www.amazon.com.au/System-Stability-Control-Paperback-Prabha/dp/0070635153/ref=sr_1_1?qid=1586581887&refinements=p_27%3APrabha+Kundur&s=books&sr=1-1) I went through the derivation of these models in previous posts. The blog post for the proportional (P) control model can be found [here](https://skreynolds.github.io/blog/2020/03/12/primary-control); and the blog post of the proportional integral (PI) control model can be found [here](http://127.0.0.1:4000/blog/2020/03/15/secondary-control).

Now is as good a time as any to have a crack at modelling - but what software to use?

As a budding engineer, of the electrical kind, I have been known to dabble in the old [MATLAB](https://en.wikipedia.org/wiki/MATLAB) from time to time. My explanation of this software is as follows: a proprietary software that does good matrices and stuff.

As a general rule I hate software which isn't open source; and I hate software which isn't open source and only runs on Windows OS even more. With that in mind, MATLAB is a perfect candidate to bear the full brunt of my crankiness given that it is neither open source AND it only runs on Windows and Apple operating systems. Having said all that, I begrudgingly accept that MATLAB *is* good for rapid prototyping, and MATLAB's Simulink is good for creating quick simulations.

I have decided to use MATLAB and Simulink to start my experimentation with the power system models. The plan is to replicate some basic power system simulation results in a couple of papers, and then if I have success doing this, I will look to port these simulations to Python. For the purposes of developing a deep reinforcement learning agent, I think that Python will be the best platform to simulation - this would allow me to take full advantage of OpenAI's open source deep reinforcement learning software architectures.

I've spun up a github repo to store this experimentation. Check it out [here](https://github.com/skreynolds/ENG720_matlab_models).