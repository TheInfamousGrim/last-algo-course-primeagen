# Graph Overview

Soooo many problems eventually become graph problems. And this is by far the largest section of algorithms.

## Contents

1. [What Are Graphs](#what-are-graphs)
2. [Graph Terms](#graph-terms)
3. [Implementation Terms](#implementation-terms)

## What Are Graphs

All trees are graphs, but not all graphs are trees.

## Graph Terms

cycle: When you start at Node(x), follow the links, and end back at Node(x).

    - It requires three nodes to be a cycle.

acyclic: A graph that contains no cycles.

connected: When every node has a path to another node.

directed: When there is a direction to the connections. Think twitter, google maps.

undirected: Not directed. Think Facebook (This may have changed)

weighted: The edges have a weight associated with them. Think maps.

dag: Directed, acyclic graph.

## Implementation Terms

node: A point or vertex on the graph.

edge: The connection betwixt two nodes.

## Time Complexity

BigO is commonly stated in terms of V and E where V stands for vertices and E stands for edges.

so O(V \* E) means that we will check every vertex, and on every vertex we check every edge.
