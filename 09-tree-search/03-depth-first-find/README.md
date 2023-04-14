# Depth First Find

Finding a node in a binary tree

## Contents

1. [How Does it Work](#how-does-it-work)
2. [Time Complexity](#time-complexity)

## How Does it Work?

The nodes on the left must be smaller than the nodes on the right!!!!!

```
<------- <= ------- 17 ------ < ------->
                   (17)
        (15)                      (50)
    (4)      (16)            (25)
                         ()        ()
```

This is very similar to a binary search on an array

```TypeScript
find(node, value): bool {
    // If there is no node return false
    if (!node) {
        return false;
    }

    // If the current node value is equal to value
    if (node.value === value) {
        return true
    }

    // If the node's value is less than the value go to the right branch
    if (node.value < value) {
        return find(node.right, value);
    }

    // Otherwise go to the left branch
    return find(node.left, value);
}
```

## Time Complexity

You might think it's O(logn).

It's actually O(h), where h stands for the height. If you have a balanced tree it's O(logn), if you have an unbalanced tree with a single very long branch it's O(n).
