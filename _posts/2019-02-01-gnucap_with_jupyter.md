---
layout: post
title: Gnucap with Jupyter
tags: simulation, gnucap, jupyter
---
It is possible to simulate electronics with GnuCAP from Jupyter. First, you need to install a recent version of Gnucap as discussed in this (GitBook)(https://mulder-patrick.gitbook.io/gnucap/). I installed Gnucap inside a Docker container derived from the Debian image.

See below some examples of the gnucap integration:

<img src="/media/images/pn_plot.PNG" />
<img src="/media/images/pygnucap.png" />


Circuit file:
```
** simulation of pn junction
Vds 1 0 DC +10V
Vgs 2 0 DC +3V
M1 1 2 0 0 nmos_enhance L=10u W=400u

* model statement (Level 1 by default)
.MODEL nmos_enhance nmos (kp=20u Vto=+2 lambda=0)

** output
.print DC V(1) I(Vds)

** analysis
.DC Vds 0V 3V 100mV

```
