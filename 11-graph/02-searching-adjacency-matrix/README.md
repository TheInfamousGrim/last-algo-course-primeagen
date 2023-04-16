# Searching an Adjacency Matrix

There are two ways to represent a graph:

- Adjacency List
- Adjacency Matrix

## Contents

1. [What is an Adjacency List](#what-is-an-adjacency-list)
2. [Adjacency Matrix](#adjacency-matrix)
3. [Basic Searches](#basic-searches)

## What is an Adjacency List

This is what an adjacency list would look like

```TypeScript
[
    [
        { to: 1, weight: 10 }
    ]
    [],
    [ { to: 0, weight: 2 } ],
    [ { ... }, { ... } ],
]
```

## Adjacency Matrix

This is a way an adjacency matrix would look like

```
[
    0, 1, 2, 3,
    0, [0 , 10, 0, 5],
    1, [0, 0, 0, 0],
    2, [],
    3, [],
 ]
```

The problem is that these require 0(V^2)

## Basic Searches

BFS and DFS still exist on a graph, and they are virtually no different than on a tree.

## Implementation of BFS on Adjacency Matrix

Let's look at the code shall we:

```TypeScript
export default function bfs(
    graph: WeightedAdjacencyMatrix,
    source: number,
    needle: number,
): number[] | null {
    // Set up our seen array
    const seen = new Array(graph.length).fill(false);

    // Set up our previous array to create our path
    const prev = new Array(graph.length).fill(-1);

    // Put our source in the seen array
    seen[source] = true;
    // Put our source in the queue
    const queue: number[] = [source];

    //
    while (queue.length) {
        // remove the current vertex from the queue
        const curr = queue.shift() as number;

        // If the current is equal to the needle break
        if (curr === needle) {
            break;
        }

        // Set up the adjacency comparison so we can compare edges
        const adjs = graph[curr];

        // We need to loop through the graph and grab an edge
        for (let i = 0; i < graph.length; ++i) {
            // If there is no edge
            if (adjs[i] === 0) {
                continue;
            }

            // If we have seen the edge
            if (seen[i]) {
                continue;
            }

            // Put the current edge into the seen array
            seen[i] = true;
            // Put edge that was just popped out of the queue into the path array
            prev[i] = curr;
            // push the edge into the queue
            queue.push(i);
        }
    }

    // Build it backwards

    // Use the needle to walk back through our path
    let curr = needle;

    // Represents our path through the graph starting at the needle to the source
    const out: number[] = [];

    // Keep doing this until we find a point that has no more parents
    while (prev[curr] !== -1) {
        // Push the current every time we see this
        out.push(curr);
        // Set this to the parent
        curr = prev[curr];
    }

    // If we did have a path from beginning to end
    if (out.length) {
        // Return the path with source and reverse it.
        return [source].concat(out.reverse());
    }

    // Return null if needle not found
    return null;
}
```
