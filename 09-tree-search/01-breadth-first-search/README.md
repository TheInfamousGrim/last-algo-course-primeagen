# Breadth First Search

We're going to use a queue to search that tree my doots

## Contents

1. [What is a Breadth First Search](#what-is-a-breadth-first-search)
2. [Time Complexity](#time-complexity)

## What is a Breadth First Search

It's the opposite of a tree traversal.

Instead of using a stack we use a queue instead.

```
                    7
            23              8
        5       4       21      15

7 -> 23 -> 8 -> 5 -> 4 -> 21 -> 15

// printed out
7, 23, 8
5, 4, 21, 15
```

## Time Complexity

Generally a depth first search should be O(N).

However when we use a JavaScript ArrayList it's O(N^2)

So use a queue data structure and use a breadth first search.

## Implementing Breadth First Search

Let's look at that code:

```TypeScript
export default function bfs(head: BinaryNode<number>, needle: number): boolean {
    // Create the queue using the binary tree
    const queue: (BinaryNode<number> | null)[] = [head];

    // While the queue length is greater than 0
    while (queue.length) {
        // Remove the first element in the queue and save it as the current value
        const curr = queue.shift() as BinaryNode<number> | undefined | null;

        // If there is no current element continue
        if (!curr) {
            continue;
        }

        // search for the needle
        if (curr.value === needle) {
            // If the needle is found return true
            return true;
        }

        // Push the left and right element into the queue if they exist
        queue.push(curr.left);
        queue.push(curr.right);
    }

    return false;
}
```
