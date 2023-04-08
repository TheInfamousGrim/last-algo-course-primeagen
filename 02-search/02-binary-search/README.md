# Binary Search

It should be O(logN).

## Contents

1. [What is It?](#what-is-it)

## What is it

If the list is ordered we can use this method.

1. We can go to the middle of the array
   - If it's the value, hey ho we've done it
   - If the value is larger then x then we half it again at the upper half of the array
   - If the value is smaller than x then we half it again at the lower bounds of the array
2. We keep doing this until we find the value or we come to the conclusion that x is not in the array.

Another important part of Big O:

- If the input halves at each step, it's likely O(LogN) or (NLogN)

## Pseudo Code

```
search(arr, low, high, needle) {
    midpoint = floored((low + high) / 2)

    value = arr[midpoint]

    while (low <= high) {
        if value = needle {
            return true
        } else if value < midpoint {
            low = midpoint + 1
        } else {
            high = midpoint - 1
        }
    }

    return false
}
```
