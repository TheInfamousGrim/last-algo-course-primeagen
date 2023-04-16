# Searching an Adjacency List

Let's implement a depth first search on an adjacency list

## Contents

1.[Implement DFS on Adjacency List](#implement-dfs-on-adjacency-list)

## Implement DFS on Adjacency List

Here's the code my doots:

```TypeScript
function walk(
    graph: WeightedAdjacencyList,
    curr: number,
    needle: number,
    seen: boolean[],
    path: number[],
): boolean {
    // Base Cases

    // If we've seen it return false
    if (seen[curr]) {
        return false;
    }

    seen[curr] = true;

    //Recurse

    //pre
    // push the current node into the path
    path.push(curr);

    // If we've found the needle return true
    if (curr === needle) {
        return true;
    }

    //recurse
    // Get the adjacency list
    const list = graph[curr];
    // Walk through the adjacency list
    for (let i = 0; i < list.length; ++i) {
        // Save the current edge
        const edge = list[i];

        // recurse finds the needle
        if (walk(graph, edge.to, needle, seen, path)) {
            // We need to stop recursing
            return true;
        }
    }

    // post
    // pop the last node from the path
    path.pop();

    return false;
}

export default function dfs(
    graph: WeightedAdjacencyList,
    source: number,
    needle: number,
): number[] | null {
    // Create a seen array
    const seen: boolean[] = new Array(graph.length).fill(false);
    // Create a path array
    const path: number[] = [];

    // Call the walk function
    walk(graph, source, needle, seen, path);

    // If the path has a length of 0 return null as no needle was found
    if (path.length === 0) {
        return null;
    }

    // Otherwise return the path
    return path;
}
```
