# Graph Degree Balancing

This repository contains a Python script that calculates the minimum number of edges needed to balance the in-degrees and out-degrees in a directed graph represented by an adjacency list.

In graph theory, **in-degree** refers to the number of edges directed towards a node, while **out-degree** refers to the number of edges directed from a node. Balancing these degrees is useful for applications such as optimizing flow networks or ensuring symmetry in directed graphs.

## Problem Overview

The script calculates the **minimum number of edges** to be added to a directed graph to balance the in-degrees and out-degrees. The process involves:
1. Calculating the out-degree for each node, which is simply the number of neighbors (outgoing edges).
2. Calculating the in-degree for each node, which is the total number of times a node is a neighbor (incoming edges).
3. Determining how many edges need to be added to balance the graph, which is the sum of absolute differences between in-degrees and out-degrees for each node.

## Script

```python
adjacency_list = {
    1: [2, 3, 5],
    2: [1, 4],
    3: [2, 5],
    4: [1, 2, 5],
    5: [3]
}

in_degrees = {}
out_degrees = {}

# Calculate in-degrees and out-degrees
for node, neighbors in adjacency_list.items():
    out_degrees[node] = len(neighbors)
    for neighbor in neighbors:
        in_degrees[neighbor] = in_degrees.get(neighbor, 0) + 1

# Calculate the minimum number of edges to add
min_edges_to_add = sum(abs(in_degrees.get(node, 0) - out_degrees.get(node, 0)) for node in set(in_degrees) | set(out_degrees))

print(f"The minimum number of edges to add is: {min_edges_to_add}")

Example Output
The minimum number of edges to add is: 2

Requirements
Python 3.6 or higher

No external libraries are required.

Applications
Graph theory and network analysis

Balancing flow networks or data pipelines

Solving optimization problems related to directed graphs

License
This project is released under the MIT License.


