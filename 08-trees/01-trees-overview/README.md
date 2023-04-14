# Trees Overview

What are trees? Don't smoke the trees. 😚🌴☁️ 🙅‍♂️

## Contents

1. [All Programming Leads to Trees](#all-programming-leads-to-trees)
2. [What Are Trees](#what-are-trees)
3. [Terminology](#terminology)

## All Programming Leads to Trees

Most complex projects that you ever work on ends up being a tree exercise.

## What Are Trees?

- Your filesystem is a tree
- The dom is a tree
- Trees are massively important in compilers. You have probably minimally heard the term Abstract Syntax Tree.
- And much more!

### Example

A tree is made up of nodes.

You could represent a node something like this:

```TypeScript
type Node<T> = {
    value: T;
    children: [];
}
```

A diagram for your brain spaces:

```
                HTML
                ( )
        child   child   child
```

So a tree is simply a serious of nodes with children.

## Terminology

Root: Your top most node. The most parent node. The First. E.

Height: The longest path from the root to the most child node. The final descendent of the root node. The next generation baby.

Binary Tree: A tree with at max two children, at least 0 children.

General Tree: A tree with 0 or more children.

Binary Search Tree: A tree in which has a specific ordering to the nodes and at most 2 children.

Leaves: A node without children.

Balanced: A tree is perfectly balanced when any node's left and right children have the same height.

Branching Factor: The amount of children a tree has.
