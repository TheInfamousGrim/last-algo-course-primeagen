# Linked List Data Structures

## Contents

1. [Weirdness](#weirdness)
2. [Singly Linked List](#singly-linked)
3. [Doubly Linked List](#doubly-linked)
4. [Insertion for a Linked List](#insertion-for-a-linked-list)
5. [Deletion for a Linked List](#deletion-for-a-linked-list)

## Weirdness

In JavaScript arrays, const a = []; is not an array. We now have a solid definition of an array, is it an array? (some answer yes)? And why not?

It's not array because you can grow it.

## What Sucks About an Array

- You can't delete something
- You can't insert something
- You cannot grow the size of the array

## What is a LinkedList

- Singly Linked
- Doubly Linked

The cool thing about linkedLists is that deletion and insertion can be very fast

## Singly Linked

a -> b -> c -> d

If we want to find the value of d we have to walk along the list till we get to d.

```
node<T> {
    val: T;
    next?: Node<T>
}
```

## Doubly Linked

Doubly linkedLists are lil bit different.

a <-> b <-> c <-> d

Each node will have reference to it's previous value if it exists and the next value if it exists.

```
node<T> {
    val: T;
    next?: node<T>;
    prev?: node<T>
}
```

## Insertion for a Linked List

a <-> b <-> c <-> d

What if wanted to insert e where b is in the doubly linkedList

Therefore:

- a needs to point to e
- b needs to point to e
- e needs to point to a
- e needs to point to b

Insertion itself O(1) time

Prepending and appending is O(1) time.

Insertion in the middle is O(n) time as you have to traverse the list

## Deletion for a Linked List

a <-> b <-> c <-> d

What if we wanted to delete c in the doubly linkedlist

Therefore:

- b would now need to point to d or
  `b = c.next`
  `b.next = c.next`
- d would now need to point to b or
  `d.prev= c.prev`
- We would remove c
  `c.prev = c.next = null`

The Deletion itself is O(1)

Deleting from the ends is O(1) time

Deleting from the middle is O(n) as you have to traverse the list

## Get a value

Getting a value is O(n) time complexity.

You have to traverse the list

Getting head or tail can become a constant operation.
