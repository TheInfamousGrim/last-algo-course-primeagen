# Tree Traversal

Attempt to visit every single node

## Contents

1. [What is a Tree Traversal](#what-is-a-tree-traversal)
2. [Pre Order Traversal](#post-order-traversal)
3. [In Oder Traversal](#in-order-traversal)
4. [Post Order Traversal](#post-order-traversal)
5. [Time Complexity for Tree Traversal](#time-complexity-for-tree-traversal)
6. [Implement a Binary Tree Pre Traversal](#implement-a-binary-tree-in-order-traversal)
7. [Implement a Binary Tree In Order Traversal](#implement-a-binary-tree-in-order-traversal)
8. [Data Structure for Tree Traversal](#what-data-structure-are-we-using-for-traversal)

## What is a Tree Traversal

So we want to visit every node

```
                7
        23              3
    5       4       18      21
```

## Pre Order Traversal

Here's the logic:

```TypeScript
visitNode()
recurseL()
recurseR()
```

So for our example we would:

- Visit 7 and print it out
- We'd recurse and visit 23 and print it out
- We'd recurse and visit 5 and print it out
- There's no more children so then we'd pop the stack and visit 4 and print it out
- There's no more children so then we'd pop the stack.
- Then we'd recurse and visit 3 and print it out.
- Then we'd recurse and visit 18 and print it out.
- There's no more children so then we'd pop the stack and visit 21 and print it out.
- There's no more children to visit so then we'd return

The output would look something like this:

`7, 23, 5, 4, 3, 18, 21`

This type of traversal is called Pre Order Traversal

## In Order Traversal

```TypeScript
recurseL()
visitNode()
recurseR()
```

The output would look a lil bit like this:

`5, 23, 4, 7, 18, 3, 21`

This type of traversal is called In Order Traversal

## Post Order Traversal

Here's the logic for a Post Order Traversal

```TypeScript
recurseL()
recurseR()
visitNode()
```

With our example, the output would look like this:

`5, 4, 23, 18, 21, 3, 7`

This type of traversal is called Post Order Traversal

## Time Complexity for Tree Traversal

It's O(n)

## Implement a Binary Tree Pre Order Traversal

Let's look at an implementation this shall we:

```TypeScript
// Recursive Function
function walk(curr: BinaryNode<number> | null, path: number[]): number[] {
    // If there is no child
    if (!curr) {
        return path;
    }

    // pre
    // Append the current node to the path
    path.push(curr.value);

    // recurse
    // We need to move left down the tree
    walk(curr.left, path);

    // We need to move right down the tree
    walk(curr.right, path);

    // post
    // Return the path once we're done recursing
    return path;
}

export default function pre_order_search(head: BinaryNode<number>): number[] {
    return walk(head, []);
}
```

Pretty simple yeah?

## Implement A Binary Tree In Order Traversal

This is very similar to the pre order. We just switch the order of where we update the path

```TypeScript
// Recursive Function
function walk(curr: BinaryNode<number> | null, path: number[]): number[] {
    // If there is no child
    if (!curr) {
        return path;
    }

    // recurse
    // We need to move left down the tree
    walk(curr.left, path);

    // pre
    // Append the current node to the path
    path.push(curr.value);

    // recurse
    // We need to move right down the tree
    walk(curr.right, path);

    // post
    // Return the path once we're done recursing
    return path;
}

export default function pre_order_search(head: BinaryNode<number>): number[] {
    return walk(head, []);
}
```

## Implement A Binary Tree Post Order Traversal

Again we just change the order where we update the path.

```TypeScript
// Recursive Function
function walk(curr: BinaryNode<number> | null, path: number[]): number[] {
    // If there is no child
    if (!curr) {
        return path;
    }

    // recurse
    // We need to move left down the tree
    walk(curr.left, path);

    // recurse
    // We need to move right down the tree
    walk(curr.right, path);

    // pre
    // Append the current node to the path
    path.push(curr.value);

    // post
    // Return the path once we're done recursing
    return path;
}

export default function pre_order_search(head: BinaryNode<number>): number[] {
    return walk(head, []);
}
```

## What data structure are we using for traversal?

We're using a stack.
