# Depth First Insert

Insert a node in an ordered binary tree

## Contents

1. [How Does it Work](#how-does-it-work)

## How Does it Work?

Remember the nodes on the left must be smaller than the nodes on the right!!!!!

```
<------- <= ------- 17 ------ < ------->
                   (17)
        (15)                      (50)
    (4)      (16)            (25)
                         ()        ()
```

This is very similar to a binary search on an array

```TypeScript
insert(node, value): bool {
    if (node.value < value) {
        if (!node.right) {
            inertion || walk
        }
    }
}
```
