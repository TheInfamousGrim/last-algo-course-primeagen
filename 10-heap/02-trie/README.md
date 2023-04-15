# Trie

You gotta keep trying man 😏.

## Contents

1. [What is a Trie](#what-is-a-trie)
2. [Example](#example)
3. [Pseudo Code](#pseudo-code)

## What is a Trie?

They are pronounced like Tree (It's named after Re"trie"val Tree).

It's a Trie tree (But people keep calling them try trees/prefix/digital tree)!

These happen SO frequently in interviews, its outstanding!

For the sake of being practical, let's get right into this!

### Autocomplete

Think of an autocomplete.

## Example

You always have a root that is empty

We're going to do an english language tree.

We're going to pretend to build a spell checker

We want to build a spell checker

```
                                ()
                        (c)             (m)
                (a)                     (a)
    isWord(t)       (r)                 (r)
          (s)  (t)  (d)                 (k)
               (t)
               (l)
               (e)
```

But How do we deal with a large set of words?

With a try we can add some more data to help with that:

- Score
- Frequency

## Pseudo Code

### Insertion

O(N) time complexity

```TypeScript
// insertion
insertion(str) {
    curr = head;
    for (c in str) {
        if (curr[c]) {
            curr = curr[c];
        } else {
            node = createNode();
            curr[c] = node;
            curr = node
        }
    }

    curr.isWord = true
}
```

### Deletion

O(N) time complexity

```TypeScript
deletion(str) {

}
```
