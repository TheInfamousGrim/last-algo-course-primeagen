# Implement Depth First Search

Let's find a node in a binary tree

## Contents

1. [How Do We Do It?](#how-do-we-do-it)

## How Do We Do It?

Let's implement the code:

```TypeScript
function search(curr: BinaryNode<number> | null, needle: number): boolean {
    // If there is no node return false
    if (!curr) {
        return false;
    }

    // If the current nodes value is equal to the needle
    if (curr.value === needle) {
        // We've found the needle return true
        return true;
    }

    // Traverse the right branch
    if (curr.value < needle) {
        return search(curr.right, needle);
    }

    // Traverse the left tree
    return search(curr.left, needle);
}

export default function dfs(head: BinaryNode<number>, needle: number): boolean {
    return search(head, needle);
}
```
