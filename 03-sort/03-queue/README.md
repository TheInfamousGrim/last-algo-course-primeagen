# Queue

Is this a data structure or an Algorithm? This is one of the most common data structures used in most languages.

## Contents

1.

## What is A Queue?

This is a specific implementation of a linked list.

A queue is simply a FIFO structure (first in first).

Head -> A -> B -> C -> D -> Tail

We also want our head to point to A.
We want our tail to point to D.

## Insertion - enqueue

We want to insert E at the end of the queue.

Head -> A -> B -> C -> D -> E -> Tail

We would need D to point to E.
we would need our tail to point to E.

```
this.tail.next = E
this.tail = E
```

## Removal - dequeue

Similar process

Head -> B -> C -> D -> E -> Tail

## Get - Peek

Find of the
