---
title: Network analysis
prev: data-description
next: text-analysis
---
The aim of our Network analysis was to find out if the PyPi network had any meaningfullnes in its structure, what the nature of the network is and if there's any significant nodes.

As mentioned in the description of the data the network is directed where a package points to its dependency.

To investigate if the PyPi network has meaningfullness it is advisable to generate a set of randomized graphs with the same underlying in- and out-degrees of each individual node in the network. This is to make sure that the assortativity which can be found is not due to any structural feature. Therefore these rules were applied to the randomization. 

1. It should not have multilinks
2. It should not have self-loops
3. It should let the in- and out-degree stay the same during node swapping

This randomization (which is also known as R-S randomization which is used to generate simple networks) was applied and 50 random graphs were generated. 

The pseudocode is provided below: 

```python
function degree_preserving_randomization( G ):
    """
    Parameters:
    - G: A directed graph.
    Returns:
    - G_rand: The degree-preserved randomized graph.
    """
    # Create a copy of the graph
    G_rand = copy(G)
    for each edge in G_rand * 10:
        # Select two sets of connected
        idx1, idx2 = random.sample(G_rand.index, 2)
        u, v = G_rand.edges[idx1]
        x, y = G_rand.edges[idx2]
        # Ensure distinct nodes
        if lenght(set([u, v, x, y])) < 4:
            continue
        # Ensure that the new edges do not exist
        if x not in G_rand.neighbors(v) and y not in G_rand.neighbors(u):
            G_rand.remove_edges_from([(u, v), (x, y)]) # Remove the old edges
            G_rand.add_edges_from([(u, y), (x, v)]) # Add the new edges
    return G_rand

```

Afterwards the assortativity was calculated for each of combination of in-out degree for each pair of nodes.
**For a node pair where Node A points to Node B:**
* In degree of Node A and in degree of Node B: in-in
* Out degree of Node A and in degree of Node B: out-in
* In degree of Node A and out degree of Node B: in-out
* Out degree of Node A and out degree of Node B out-out

This gives the resulting plots:

<img src="/images/Assortativity_lineplot_R_S.png" width="800" />

The out-in assortativity of the random graphs show that there is some structural disassortativity in the graph structure however this does not explain the even higher amount of disassortativity of out-in nodes.
 The other types of assortativity appear to be neutral according to the random graphs. However the out-out degree does also display some assortativity. Below there is another plot of the disassortativity:

<img src="/images/Assortativity_column_R_S.png" width="800" />

This plot shows that the random graphs are generelly distributed in the same way while the PyPi network is significantly different. Recall that there's 50 random models so it can be assumed that they would follow the central limit theorem. Their standard deviation is not high enough to encompass the PyPi network. I.e. the PyPi network is statistically significantly different from the random networks. 

This means that the PyPi network dissplays very clear disassortativity in out-in degree.

**What are the implications of this?**

So in the case of the context of the PyPi network this means that when a node A with many dependencies is linked to a node B that will generally have fewer packages depending on it. 

This can also be said in the reverse manner that a Package A with many packages depending on it will be pointed on by a package with few dependencies.

A concrete example could be the package _Numpy_ which has about 3.500 packages depending on it. These packages will generally not be depending on very many other packages. While some other package f.ex. _jupyter-events_ which has only 17 packages depending on it, will be the dependency of packages which depend on more packages. So these 17 packages will depend on more packages.

-----

Finally it is also important to look at the relationship between closeness and degree of the nodes:

<img src="/images/Closeness_vs_Degree.png" width="800" />

There is a linear relationship between closeness centrality and degree meaning that the higher the degree of a node the closer it is to all other nodes. So to contextualize this a package such as _numpy_ or _requests_ which both have around 3.500 packages depending on them will both be very central and it would be easy to reach other nodes starting from these nodes. 