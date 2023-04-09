# Stack

Node like algorithm

## Contents

1.

## What is it?

```
Node<T>
    Value: T
    next?: Node<T>
    prev?: Node<T>
```

rather than a queue:

A -> B -> C -> D

This is a stack:

Tail <- A <- B <- C <- D <- Head

A stack is a FILO (First in Last Out)

You can do three types of operations:

- Push (add a node to the head of the stack)
- Pop (remove a node from the head of the stack)
- Peek (Look at the head of the stack)
