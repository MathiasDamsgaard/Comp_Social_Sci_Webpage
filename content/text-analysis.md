---
title: Text analysis
prev: network-analysis
---


The last step of the analysis was about identifying communities within the large network of all the python packages and their requirements and investigate if packages that are related to similar tasks or fields within programming, form meaningful substructures in the network. To start this analysis the first task was identify communities within the network. Since the network is relatively large with around * nodes, we use the Louvain method for community detection as it performs well on large dataset and is shown that it has a very good accuracy in terms of decomposing the network in communities that have a modularity close to the optimal one. 
The algorithm follows a greedy optimization approach for finding communities. It initially identifies small communities by optimizing modularity locally for all nodes. Each of these small communities is then treated as a single unit and the algorithm is repeated until a certain threshold of gain in modularity is exceeded. Using the algorithm on our network, we find around 430 communities and a total modularity of around 0.52, indicating that the algorithm finds meaningful communities. 
However, out of the total number of communities, only a few of them are large (around 5) and contain nodes in the thousands. There are also some smaller communities with nodes in the hundreds, and lastly, many very small communities that have nodes ranging from around 2 to 10. For further analysis, we will focus on the top 10 largest communities.
Taking a closer look at some of the largest communities, we can explore if it is possible to identify different fields within the network based on the packages alone. The following lists the 10 “most important” packages within the three largest communities based on their in-degree:

1. numpy, pandas, matplotlib, scipy, tqdm, pillow, scikit-learn, pip, torch, python
2. pytest, pytest-cov, coverage, flake8, twine, setuptools, black, sphinx, wheel, mypy
3. requests, click, beautifulsoup4, lxml, flask, boto3, plotly, python-dotenv, future, bokeh

Looking at these packages, it appears that the communities formed indeed relates to different subfields within programming. For example, the first community seems to be centered around scientific computing and machine learning, with packages like numpy, pandas, matplotlib, scipy, scikit-learn, and torch. The second community seems to be focused on testing and code quality, with packages like pytest, pytest-cov, coverage, flake8, and mypy. The third community seems to be related to web scraping and web development, with packages like requests, click, beautifulsoup4, lxml, and flask.
To try to obtain a deeper understanding of each community, we conducted a textual analysis of the packages’ README files using TF-IDF. By analyzing the words used in these files, we can gain further knowledge about what the packages in the communities are typically used for. The first step was to tokenize the text by removing any stopwords, punctuation, and stemming the words across all the README files. These were then used in the analysis where the top TF-IDF words for each community was computed. To visualize the results, word clouds of the biggest 10 communities with their TF-IDF words where created. In the following plot the word cloud for the largest community along with a listing of the top 3 packages within the community based on in-degree can be seen. Similar word cloud plots for the rest of the top 10 communities can be seen in the explainer notebook.  

Insert plot

Skriv om wordclouds

