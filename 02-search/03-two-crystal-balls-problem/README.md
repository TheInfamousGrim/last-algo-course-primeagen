# The Two Crystal Ball Problem

Given two crystal balls that will break if dropped from a high enough distance, determine the exact spot in which it will break in the most optimized way.

## How do we solve it?

```
twoCrystalBalls(arr) {
    // we want to create a jump amount
    jumpAmount = Math.floor(Math.sqrt(arr.length))

    // We then set a pointer to the value of the jump amount
    i = jumpAmount

    // We then do the first loop through the array
    // We jump through the array by the jump amount
    for (i; i < arr.length; i += jumpAmount) [
        // If the value at the index is equal to a boolean then we break the array
        if arr[i] {
            break;
        }
    ]

    // Move back by the jump amount
    i -= jumpAmount

    // Loop through the array from the point before the ball broke
    for (let j = 0; j < jumpAmount && i < arr.length; ++j, ++i) {
        if arr[i] {
            return i;
        }
    }

    return -1;
}
```
