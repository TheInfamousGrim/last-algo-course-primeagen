# Bubble Sort

## How do solve this?

```
bubbleSort(arr) {
    // We are looping through the whole array
    for (i = 0; i < arr.length; ++i) {
        // For each value of the array we need to loop through and bubble up the largest value to the end of the array
        // This means we never need to loop to the end of the array
        // After the largest value has bubbled up to the end of the array we can subtract that from the inner loop
        for (j = 0; j < arr.length - 1 - i; ++j) {
            // If the ith value is greater than the jth value then we swap em
            if (arr[i] > arr[j]) {
                swap(i, j)
            }
        }
    }
}
```
