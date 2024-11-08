---
title: Home Page
layout: single
next: data-description
---
This project works to investigate a network constructed of _python packages' dependencies_ on each other. This is based on the available packages on [python package index (PyPi)](https://pypi.org/). Inspiration of this project idea comes from seeing an older dataset on [Netzschleuder](https://networks.skewed.de/net/python_dependency) made by Kevin Gullikson. His [original blogpost](https://kgullikson88.github.io/blog/pypi-analysis.html) is from 2016, and will therefore be used as a baseline for comparing the networks on a timescale.
<img src="/images/pypi.svg" width="200">

The resulting network will be analysed based on theory for a directed network, where a package point to another package if the first package is dependent on the second one. This information was collected from the individual packages githubs. Further information on the data acquisition can be found in the data tab.

This research was conducted for investigating how the package library in Python has evolved over the years and further investigate which packages seem to be the hubs of all other packages. Creating libraries is a big part of programming to help make functions easier to use across files and users, and thus the goal with this website is to shine light on the insights gained when looking at the connections between the libraries and the groups these create.
By also analysing the text available in README files, understand of how programmers formulate themselves when writing documentation for their code, and the variation across different groups can be visualized. This is the main points of the research on this website, and the authors hope you find the reading enjoyable.

In the end the research showed some interesting results in both the network and textual analysis. The network analysis finds that the PyPi network is not different from a random network, and that it tends to be disassortative. Additionally, a trait in the network is the way that packages link to each other, where packages with high dependency is often a requirement from packages that aren't that important. Further, it was found that there have been a big change in how packages on PyPi now point to each other, and which packages have become the most important and dependent across python.

On the other hand, the textual analysis showed some interesting groupings of the packages, where it is possible to understand why certain packages were selected to be partitioned together. However, the wordclouds where more obscure, but some terms did come across with some meaning to the groups.

Further, links are provided to a webbased visual representation of the [notebook](explainer-notebook.html), which contain all the relevant code along with clarifications and explanations on the workflow and decisions taken. The [repository](https://github.com/MathiasDamsgaard/Comp_Social_Sci_Assignments) can be found by following the linked icons at the bottom of the page, togehter with shared versions of the relevant [data files](https://drive.google.com/drive/folders/1ds2DuMk6-3qzciHKSTfHVpAQfmKQm407?usp=sharing). However, this webpage is being run through [this repository](https://github.com/MathiasDamsgaard/Comp_Social_Sci_Webpage) instead.