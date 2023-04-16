# Dijkstra's Shortest Path

Get the shortest and most efficient path

## Contents

1. [What is it?](#what-is-it)
2. [Dijkstra's Implementation Bad Runtime](#dijkstras-implementation-bad-runtime)

## What is it?

It's part of a family of algorithms that are greedy.

```
prev = [-1, ...]
seen = [false, ...]
dists = [infinity, ..., 0]

while hasUnvisted() {
    low = getLowestUnseen()
    seen[low] = true

    for edge in low {
        if seen[edge] {
            continue
        }
        dist = dists[low] + edge.weight;

        if dist < dists[edge] {
            low = prev[edge]
            dist = dists[edge]
        }
    }
}
```

## Dijkstra's Implementation Bad Runtime

```TypeScript
function hasUnvisted(seen: boolean[], dists: number[]): boolean {
    // Check if you have visited a node
    return seen.some((s, i) => !s && dists[i] < Infinity);
}

function getLowestUnvisted(seen: boolean[], dists: number[]): number {
    // Let the index = -1
    let idx = -1;
    // Set the lowest distance to infinity
    let lowestDistance = Infinity;

    // Walk through the seen array
    for (let i = 0; i < seen.length; ++i) {
        // If it has been seen continue
        if (seen[i]) {
            continue;
        }

        // If the lowest distance is greater than distances in the distances array
        if (lowestDistance > dists[i]) {
            // set the lowest distance equal to the index of the distances array
            lowestDistance = dists[i];
            // Set the current idx to i
            idx = i;
        }
    }

    // Return the lowest distance's index
    return idx;
}

export default function dijkstra_list(
    source: number,
    sink: number,
    arr: WeightedAdjacencyList,
): number[] {
    // Create the seen array
    const seen = new Array(arr.length).fill(false);
    // Create a previous destination array
    const prev = new Array(arr.length).fill(-1);
    // Create the distances array
    const dists = new Array(arr.length).fill(Infinity);

    // Set the source distance to be zero
    dists[source] = 0;

    // While there are nodes that have not been visited
    while (hasUnvisted(seen, dists)) {
        // Set the current distance to the lowest unvisited distance
        const curr = getLowestUnvisted(seen, dists);

        // Update the seen array with the current distance
        seen[curr] = true;

        // Now we go through every edge
        // This will give us a list of our edges
        const adjs = arr[curr];
        // Go through each edge
        for (let i = 0; i < adjs.length; ++i) {
            // Get the current edge
            const edge = adjs[i];

            // If we've seen this edge continue
            if (seen[edge.to]) {
                continue;
            }

            // Get the distance from our current item to the next item
            const dist = dists[curr] + edge.weight;
            // If our current distance is smaller than the distance in our distance array
            if (dist < dists[edge.to]) {
                // Update our distance array
                dists[edge.to] = dist;
                // Update our previous destination array
                prev[edge.to] = curr;
            }
        }
    }

    // Set the output to an empty number array
    const out: number[] = [];
    // Set the current to the sink
    let curr = sink;

    // While the previous destinations with the index of current exists
    while (prev[curr] !== -1) {
        // push the current index into the output array
        out.push(curr);
        // update the current array to the previous node
        curr = prev[curr];
    }

    // push the source node to the output array
    out.push(source);

    // Reverse the output array and return it
    return out.reverse();
}
```

What would the runtime be for this algorithm? O(v^2 + E). Pretty bad yeah?

## Improved Dijkstra's Algorithm

Our updated runtime would be O(logV(V + E)).
