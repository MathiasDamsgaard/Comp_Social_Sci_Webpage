---
title: Home Page
layout: single
next: data-description
---
This project works to investigate a network constructed of _python packages' dependencies_ on each other. This is based on the available packages on [python package index (pypi)](https://pypi.org/). Inspiration of this project idea comes from seeing an older dataset on [Netzschleuder](https://networks.skewed.de/net/python_dependency) made by Kevin Gullikson. His [original blogpost](https://kgullikson88.github.io/blog/pypi-analysis.html) is from 2016, and will therefore be used as a baseline for comparing the networks on a timescale.
<img src="/images/pypi.svg" width="200">

The resulting network will be analysed based on theory for a directed network, where a package point to another package if the first package is dependent on the second one. This information was collected from the individual packages githubs. Further information on the data acquisition can be found in the data tab.

This research was conducted for investigating how the package library in Python has evolved over the years and further investigate which packages seem to be the hubs of all other packages. Creating libraries is a big part of programming to help make functions easier to use across files and users, and thus the goal with this website is to shine light on the insights gained when looking at the connections between the libraries and the groups these create.
By also analysing the text available in README files, understand of how programmers formulate themselves when writing documentation for their code, and the variation across different groups can be visualized. This is the main points of the research on this website, and the authors hope you find the reading enjoyable.

In the end the research showed some interesting results in both the network and textual analysis.

Further, links are provided to a webbased visual representation of the [notebook](explainer-notebook.html), which contain all the relevant code along with clarifications and explanations on the workflow and decisions taken. The [repository](https://github.com/MathiasDamsgaard/Comp_Social_Sci_Assignments) can be found by following the linked icons at the bottom of the page, togehter with shared versions of the relevant [data files](https://drive.google.com/drive/folders/1ds2DuMk6-3qzciHKSTfHVpAQfmKQm407?usp=sharing). However, this webpage is being run through [this repository](https://github.com/MathiasDamsgaard/Comp_Social_Sci_Webpage) instead.