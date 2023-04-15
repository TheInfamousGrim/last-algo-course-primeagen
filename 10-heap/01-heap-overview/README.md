# Heap Overview

A heap can also be known as a priority queue.

## Contents

1. [What is a Heap](#what-is-a-heap)
2. [What Does This Look Like](#what-does-this-look-like)
3. [Cool Characteristics](#cool-characteristics)
4. [Heap Implementation](#heap-implementation)
5. [Time Complexity](#time-complexity)
6. [Careful About Garbage](#careful-about-garbage)

## What is a Heap?

This is a very important data structure.

It's a Binary Tree where every child and grand child is smaller (MaxHeap) or larger (MinHeap) than the current node.

- Whenever a node is added, we must adjust the tree.
- Whenever a node is deleted, we must adjust the tree.
- There is no traversing the tree!!!

## What Does This Look Like

Heaps maintain a weak ordering.

### MinHeap

In the case of the MinHeap as long as the children are larger than the parent it doesn't matter what size they are.

Heap is always a complete tree. This means it's always adding from left to right.

```
                                (50)
                (71)                            (100)
        (101)           (80)            (200)               (101)
    (200)
```

You would assume that the tree's primitive is node based? Well that's not quite true.

We Give an index to each one of our nodes. That means we can store the tree in an array.

### Data

`[50, 71, 100, 101, 80, 200, 101, 200, 201]`

### Indexes

`[0,  1,  2,   3,   4,  5,   6,   7,   8]`

### Insertion

How doe we insert then?

If we want to insert a child to the left branch it's 2i + 1 where i is the parent index.

If we want to insert a child to the right branch it's 2i + 2 where i is the parent index.

However this is only the generic case for going down the tree.

What about going up the tree?

It's simply math.floor((i - 1) / 2) to insert a parent node for the left child node.

Math.Floor((i - 2) / 2) to insert a parent node for the right child node.

Insertion at the end?

Just get the length of the array list.

## Cool Characteristics

- It is self balancing
  - It always maintains a perfectly balanced binary tree
- It can be used for priority
  - Thread structure
- Most fun data structure to implement, but easy to get wrong!

## Heap Implementation

Here's an implementation of a basic heap

```TypeScript
export default class MinHeap {
    public length: number;
    private data: number[];

    constructor() {
        this.data = [];
        this.length = 0;
    }

    insert(value: number): void {
        // Insert the data at the end of the heap
        this.data[this.length] = value;
        // Heapify Up the heap to insert the data at the correct place in the heap
        this.heapifyUp(this.length);
        // Increase the length
        this.length++;
    }
    delete(): number {
        // If there is nothing in the heap
        if (this.length === 0) {
            // Return - 1
            return -1;
        }

        // The data to be deleted
        const out = this.data[0];
        // Decrement the length of the heap
        this.length--;
        // If there will be nothing left in the heap after deletion
        if (this.length === 0) {
            // Set the data to an empty array list
            this.data = [];
            // Return the deleted data
            return out;
        }

        // Set the data at the start of the heap equal to zero
        this.data[0] = this.data[this.length];
        // Bubble down the heap
        this.heapifyDown(0);
        // Return the deleted data
        return out;
    }

    // Bubble down data that is smaller than the parent node
    private heapifyDown(idx: number): void {
        const leftIndex = this.leftChild(idx);
        const rightIndex = this.rightChild(idx);

        // Check if the we're looking at data that doesn't exist
        if (leftIndex >= this.length || idx >= this.length) {
            return;
        }

        // Get the value of the left index
        const leftValue = this.data[leftIndex];
        // Get the value of the right index
        const rightValue = this.data[rightIndex];
        // Get the value of the data to be moved down
        const value = this.data[idx];

        // Move value down the right node
        // check if the left value is greater than the right value
        // And check if the value to be moved down is greater than the right value
        if (leftValue > rightValue && value > rightValue) {
            // Swap the values
            this.data[idx] = rightValue;
            this.data[rightIndex] = value;
            // Move the right index down the heap
            this.heapifyDown(rightIndex);
            // Move value down the left node
            // Check if the right value is greater than the left value
            // And if the value to be moved down is greater than the left value
        } else if (rightValue > leftValue && value > leftValue) {
            // Swap the values
            this.data[idx] = leftValue;
            this.data[leftIndex] = value;
            // Move the left index down the heap
            this.heapifyDown(leftIndex);
        }
    }

    // Bubble up data that is larger than the parent node
    private heapifyUp(idx: number): void {
        // If the index is equal to zero
        if (idx === 0) {
            // Stop recursing
            return;
        }

        // Save the parent
        const parent = this.parent(idx);
        // Get the parent value
        const parentValue = this.data[parent];
        // Get the value of the data to be bubbled up
        const value = this.data[idx];

        // If the parent value is greater than the bubble value
        if (parentValue > value) {
            // Set the current data to the parent value
            this.data[idx] = parentValue;
            // Set the data for the parent to the bubble value
            this.data[parent] = value;
            // Recurse baby
            this.heapifyUp(parent);
        }
    }

    // Private method for finding the parent of an index
    private parent(idx: number): number {
        return Math.floor((idx - 1) / 2);
    }

    // find the left child of a parent index
    private leftChild(idx: number): number {
        return idx * 2 + 1;
    }

    // Find the right child of a parent index
    private rightChild(idx: number): number {
        return idx * 2 + 2;
    }
}

```

## Time Complexity

It's always O(logN).

## Careful About Garbage

The previous values in the array remain unless you null them out.
