---
layout: post
title: "modelling the turbine"
date: 2020-03-10
---

When looking at a single area power system, there are three main components that the literature has a tendency to focus on:

* **Governor**: used for controlling the angular velocity (and frequency) of the system;
* **Turbine**: this is the steam turbine which provides the mechanical torque to drive the generator; and
* **Generator load**: desciribes the electrical power that is produced and the electrical torque from connected loads. 

This post will cover the basics of how the literature models the turbine and the generator-load, and will draw heavily from Kothari's awesome book: *Modern Power Systems Analysis*.

## turbine model