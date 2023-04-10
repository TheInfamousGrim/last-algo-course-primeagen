# Recursion

All work and no recursion makes jack a recurrent boy...
All work and no recursion makes jack a recurrent boy...
All work and no recursion makes jack a recurrent boy...
All work and no recursion makes jack a recurrent boy...
All work and no recursion makes jack a recurrent boy...
All work and no recursion makes jack a recurrent boy...
All work and no recursion makes jack a recurrent boy...
All work and no recursion makes jack a recurrent boy...

## Contents

1.[What is it?](#what-is-it) 2. [The Simplest Form](#the-simplest-form-of-recursion)

## What is it?

It's a function that calls itself until the problem is solved. This usually involves what is referred to as the "base case". A base case is the point in which the problem is solved at.

### Recursion is Hard Man 🥵

It's super tough to get at first. But once you understand it becomes trivial.

## The simplest form of recursion

This is simply summing the numbers from one to n.

```TypeScript
function foo(n: number): number {
    // Base Case
    if (n === 1) {
        return 1;
    }

    // Now we shall recurse
    return n + foo(n - 1);
}
```

The base case is super important!!!! You don't want to recurse infinitely. Unlike with an iterable you have to know what the first value is going to be.
