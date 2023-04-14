# Search Practice

This used to be a very common question in interviews!

## Contents

1. [The Question](#the-question)
2. [Which Search Algo Should We Use](#which-binary-search-algorithm-should-we-use)
3. [Implement Binary Tree Comparison](#implement-binary-tree-comparison)

## The Question

Compare two binary trees to see if they are equal in both shape and structure

Example:

```
            5                   5
        3       0x45        3       0x45
```

## Which Binary Search Algorithm Should We Use?

We should use depth first search

## Implement Binary Tree Comparison

Let's look at the code:

```TypeScript
export default function compare(
    a: BinaryNode<number> | null,
    b: BinaryNode<number> | null,
): boolean {
    // If they are both equal to null then they are equal
    if (a === null && b === null) {
        return true;
    }

    // If one of them is null and the other is not they are not equivalent
    if (a === null || b === null) {
        return false;
    }

    // IF the values aren't equivalent then they are not equal to each other
    if (a.value !== b.value) {
        return false;
    }

    // Both branches need to return true
    return compare(a.left, b.left) && compare(a.right, b.right);
}
```
