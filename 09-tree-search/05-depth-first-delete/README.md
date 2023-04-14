# Depth First Delete

This is the hardest to do right.

## Contents

1. [How Does This Work](#how-does-this-work)

## How Does This Work?

```
                                (15)
                (7)                             (51)
        (4)             x               (25)            (160)
    x       x                       x          (37)  x         x
                                            x         x
```

This is pretty complicated to code but the very basic pseudo code would look like this:

```TypeScript
function delete(node, value): node {
    // Case 1) No Child
        // delete

    // Case 2) One Child
        // set parent to child

    // Smallest
        // On large side

    // Largest
        // On small side
}
```
