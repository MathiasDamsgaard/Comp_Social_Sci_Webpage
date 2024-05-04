---
title: Network analysis
prev: data-description
next: text-analysis
---
The aim of our Network analysis was to find out if the Pypi network had any meaningfullnes in its structure, what the nature of the network is and if there's any significant nodes.

As mentioned in the description of the data the network is directed where a package points to its dependency.

To investigate if the Pypi network has meaningfullness it is advisable to generate a set of randomized graphs with the same underlying in- and out-degrees of each individual node in the network. This is to make sure that the assortativity which can be found is not due to any structural feature. Therefore these rules were applied to the randomization. 

1. It should not have multilinks
2. It should not have self-loops
3. It should let the in- and out-degree stay the same during node swapping

This randomization (which is also known as R-S randomization which is used to generate simple networks) was applied and 50 random graphs were generated. 

The pseudocode is provided below: 

```python
function degree_preserving_randomization( G ):
    """
    Perform degree-preserving randomization of a directed graph.

    Parameters:
    - G: A directed graph.

    Returns:
    - G_rand: The degree-preserved randomized graph.

    Prerequisites:
    - The input graph G should be a directed graph.
    - The graph G should have nodes and edges defined.
    """

    # Create a copy of the graph
    G_rand = copy(G)

    # For each swap
    for eahc edge in G_rand * 10:
        # Select two sets of connected
        idx1, idx2 = random.sample(G_rand.index, 2)
        u, v = G_rand.edges[idx1]
        x, y = G_rand.edges[idx2]

        # Ensure distinct nodes
        if len(set([u, v, x, y])) < 4:
            continue

        # Ensure that the new edges do not exist
        if x not in G_rand.neighbors(v) and y not in G_rand.neighbors(u):
            # Remove the old edges
            G_rand.remove_edges_from([(u, v), (x, y)])

            # Add the new edges
            G_rand.add_edges_from([(u, y), (x, v)])

            # Update the edges
            G_rand.edges[idx1] = (u, y)
            G_rand.edges[idx2] = (x, v)

    return G_rand

```

Afterwards the assortativity was calculated for each of combination of in-out degree for each pair of nodes.
**For a node pair where Node A points to Node B:**
* In degree of Node A and in degree of Node B: in-in
* Out degree of Node A and in degree of Node B: out-in
* In degree of Node A and out degree of Node B: in-out
* Out degree of Node A and out degree of Node B out-out

Thise gives the resulting plots:

<img src="/images/Assortativity_lineplot_R_S.png" width="800" />


<img src="/images/Assortativity_column_R_S.png" width="800" />

<img src="/images/Closeness_vs_Degree.png" width="800" />