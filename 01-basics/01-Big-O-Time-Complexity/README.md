# Big O Time Complexity

The first thing and most important thing to understand algorithm performance

## Contents

1. [What is Big O](#what-is-big-o)
2. [Why do We Use It?](#why-do-we-use-it)
3. [How can you tell the complexity?](#how-can-you-tell-the-complexity)
4. [Practical vs Theoretical Differences](#practical-vs-theoretical-differences)
5. [O(N) Always Considers Worst Case](#in-bigo-we-often-consider-the-worst-case)
6. [O(N^2)](#on2)
7. [O(N^3)](#on3)
8. [O(NLogN)](#onlogn)
9. [O(LogN)](#ologn)

## What is Big O?

Time and space complexity pretty much.

Big O is a way to categorize your algorithms time or memory requirements based on input. It is not meant to be an exact measurement. It will not tell you how many CPU cycles it takes, instead it is meant to generalize the growth of your algorithm.

e.g.

> When someone says Oh of N, they mean your algorithm will grow linearly based on input.

## Why do we Use it?

Often it will help us make decisions about what data structures and algorithms to use. Knowing how they will perform can greatly help create the best possible program out there.

### A Nice little example

First, lets consider the following code.

```TypeScript
function sum_char_codes(n: string): number {
    let sum = 0;
    for (let i = 0; i < n.length; ++i) {
        sum += n.charCodeAt(i);
    }

    return sum;
}
```

This is really easy if you know Big O, **It's O(n)**

### To say it Differently

As your input grow, how fast does computation or memory grow?

**Important Concepts**

1. growth is with respect to the input

**In the Real World**
Obviously memory growing is not computationally free, but in the matter of thinking about algorithms, we don't necessarily think about that.

In languages like Go or JavaScript you pay even heavier penalties because the memory can be kept around, grows faster, and causes complete halts in your program for cleanup.

## How can you tell the complexity?

Simplest trick is to look for loops

```TypeScript
function sum_char_codes(n: string): number {
    let sum = 0;
    for (let i = 0; i < n.length; ++i) {
        sum += n.charCodeAt(i);
    }

    return sum;
}
```

### What is the running time?

```TypeScript
function sum_char_code(n: string): number {
    let sum = 0;
    for (let i = 0; i < n.length; ++i) {
        sum += n.charCodeAt(i);
    }
    for (let i = 0; i < n.length; ++i) {
        sum += n.charCodeAt(i);
    }

    return sum;
}
```

O(n)

ALWAYS DROP CONSTANTS!!!!!!!!!

**Important Concepts**

1. Growth is with respect to the input
2. Constants are dropped

O(2N) => O(N) and this makes sense. That is because Big O is meant to describe the upper bound of the algorithm (the growth of the algorithm). The constant becomes irrelevant.

Take the following:

N = 1,O(10N) = 10,O(N^2) = 1

N = 5,O(10N) = 50,O(N^2) = 25

N = 100,O(10N) = 1000,O(N^2) = 10 000 // 10x bigger

## Practical vs Theoretical Differences

Just because N is faster than N^2, doesn't mean practically its always faster for smaller input.

Remember, we drop constants. Therefore O(100N) is faster than O(N^2) but practically speaking, you would probably win for some small set of input.

## O(N) Always Considers Worst Case

```TypeScript
function sum_char_code(n: string): sting {
    let sum = 0;
    for (let i = 0; i < n.length; ++i) {
        const charCode = n.charCodeAt(i);
        // Capital E
        if (charCode === 69) return sum;

        sum += charCode;
    }

    return sum;
}
```

The runtime of this algorithm is O(N) Why?

### In BigO we often consider the worst case

Especially in interviews (I have never been asked for best, average, and worst case, just another worst case).
E = 69
Therefore any string with E in it will terminate early (Unless E is the last item in the list).
ITS STILL O(N)

### Important Concepts

1. Growth is with respect to the input
2. Constants are dropped
3. Worst case is usually the way we measure

## O(N^2)

```TypeScript
function sum_char_codes(n: string): string {
    let sum = 0;
    for (let i = 0; i < n.length; ++i) {
        for (let j = 0; j < n.length; ++j) {
            sum += charCode;
        }
    }

    return sum;
}
```

## O(N^3)

```TypeScript
function sum_char_codes(n: string): string {
    let sum = 0;
    for (let i = 0; i < n.length; ++i) {
        for (let j = 0; j < n.length; ++j) {
            for (let k =0; k < n.length; ++k) {
                sum += charCode;
            }
        }
    }

    return sum;
}
```

## O(nLogn)

Quicksort (We're going to look at this in the course)

- Half the amount of space you need to search, but you need to go every space at least once

## O(logn)

Binary search tree

- Half the total amount of input you need to search

There is one weird problem as well, O(srt(N))

## Why so Obviated?

There are other resources out there to dive deep into Big O Notation. Look up freeCodeCamp etc.

We're just going to going to explore run times of algorithms this is a very practical approach.

## Space The Final Frontier

We pretty much won't be going over space in this course. Just not something we will be discussing. I find this less consequential in daily life considering I see things like this.

// Or whatever it is in react
// O(N) time + O(N) space! COUNT ME IN

```TypeScript
return <Component
...props />
```
