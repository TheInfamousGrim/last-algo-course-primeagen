# Quick Sort

The fastest way to sort your data

## Contents

1. [What is Divide and Conquer](#what-is-divide-and-conquer)
2. [What is Quicksort](#what-is-quicksort)
3. [What is the Time Complexity](#what-is-the-time-complexity-for-this-algorithm)
4. [Implementation of Quicksort](#implementation-of-quicksort)

## What is Divide and Conquer

Being able to split your input into 3 chunks, 4 chunks, 5 chunks etc. and then go over those smaller subsets and solve things faster.

It becomes progressively smaller until you reach 1.

## What is Quicksort

Quicksort divides and conquers:

1. It picks an element in an array which we call the pivot
   - Po is the first pivot point

```
[           <--  Po -->          ]   P
O     P1                 P2      N
^
|

^
|
```

2. Then we recursively pick another pivot between each pivot and it will look something like this:

```
                        [0, ..., 31]
                [0 - 15]            [17 - 31]
                   8                    24
         [1 - 7]        [9 - 15]
            8              12
     [1 - 3] [5 - 7] [9 - 11] [13 - 15]
        2       6       10        14
```

3. Then we sort the elements and once they've been sorted we pop the stack until the whole array has been sorted.

## What is the time complexity for this algorithm?

Our running time for this is going to be O(nlogn)

### What is the worst case?

A reverse sorted array!

`[10, 9, 8, ... 1]`

This would be O(n^2)

So the time complexity is somewhere between O(nlogn) <= O(n^2)

## Implementation of Quicksort

The quicksort algorithm can be split into two separate parts:

1. The Partition
2. The Quicksort itself

Let's start with the partition:

```TypeScript
function partition(arr: number[], lo: number, hi: number): number {
    // We select the element to pivot of
    // In this case for simplicities sake we use the last index
    const pivot = arr[hi];

    // We create a mutable variable that starts at negative 1 by using the low
    let idx = lo - 1;

    // We then need to walk from the low to the high but not including the high as it's the pivot
    for (let i = lo; i < hi; ++i) {
        // We need to compare each element to the pivot
        if (arr[i] <= pivot) {
            // increment the index
            idx++;
            // Create a temporary variable that will be used for swapping
            const tmp = arr[i];
            // We swap the element at the ith index with the element at the idx index
            arr[i] = arr[idx];
            // We then swap the element at the idx index with the temporary variable
            arr[idx] = tmp;
        }
    }

    // After we've done the swapping we need to put our pivot where the pivot index is

    // Increment the idx once more
    idx++;
    // Now we swap the values
    arr[hi] = arr[idx];
    arr[idx] = pivot;

    // Finally return the pivot index
    return idx;
}
```

Now let's look at the quicksort (the recursive function):

```TypeScript
function qs(arr: number[], lo: number, hi: number): void {
    // Base Case
    // Once we get to the point where lo and hi meet we need to stop recursing
    if (lo >= hi) {
        return;
    }

    // We need our pivot index
    const pivotIdx = partition(arr, lo, hi);

    // Then we we recursively call the quicksort algorithm

    // We go from the low and up to but not including the pivot
    qs(arr, lo, pivotIdx - 1);
    // We go from one above the pivot to the high
    qs(arr, pivotIdx + 1, hi);
}
```

Putting it all together in our quicksort function:

```TypeScript
export default function quick_sort(arr: number[]): void {
    // Quicksort
    qs(arr, 0, arr.length - 1);
}
```
