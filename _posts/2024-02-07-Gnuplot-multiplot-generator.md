---
layout: post
title: Gnuplot Multiplot Generator
date: 2024-02-07 07:00:00
description: Python script to generate gnuplot multiplot settings
tags: python gnuplot
categories: plots
---
A very usefull Gnuplot template-script generator for easy multiplot setup written in Python.

This template generator was written to easily setup Gnuplot multiplots with non-standard paddings and margins between the plots, e.g. for **placing graphs right next to each other** when they share their X- and Y-axes.

This can be implemented in Gnuplot by manually setting individual margins `tmargin`, `bmargin`, `lmargin` and `rmargin` for each graph of the multiplot canvas as explained [here](http://www.gnuplotting.org/multiplot-placing-graphs-next-to-each-other/).

Author of this usefull script is <a href='https://github.com/stefan-wr'> Stefan Wraase </a>.
