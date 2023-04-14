# prepend, insertAt & append

The nice ones

## Contents

1. [Let's Implement a Doubly Linked List](#lets-implement-a-doubly-linked-list)
2. [Prepend](#prepend)
3. [insertAt](#insertat)

## Let's Implement a Doubly Linked List

We're going to implement this interface

```TypeScript
interface LinkedList<T> {
    get length(): number;
    insertAt(item: T, index: number): void;
    remove(item: T): T | undefined;
    removeAt(index: number): T | undefined;
    append(item: T): void;
    prepend(item: T): void;
    get(index: number): T | undefined;
}
```

Let's initialize our linked list class first of all:

```TypeScript
// The type for the nodes in the linked list
type Node<T> = {
    value: T;
    prev?: Node<T>;
    next?: Node<T>;
}

class DoublyLinkedList<T> {
    // types for the linked list
    public length: number;
    private head?: Node<T>;
    private tail?: Node<T>;

    constructor() {
        // The length of the linked list at the start is 0
        this.length = 0;
        // The head is currently undefined
        this.head = undefined;
        this.tail = undefined;
    }
}
```

## Prepend

We want to add an item at the start of our linked list.

Let's look at an implementation of that:

```TypeScript
type Node<T> = {
    value: T;
    prev?: Node<T>;
    next?: Node<T>;
}

class DoublyLinkedList<T> {
    public length: number;
    private head?: Node<T>;
    private tail?: Node<T>;

    constructor() {
        this.length = 0;
        this.head = undefined;
        this.tail = undefined;
    }

    prepend(item: T): void {
        // Create the node with the value
        const node = { value: item } as Node<T>

        // Increment the list length
        this.length++;

        // If there is nothing in the linked list
        if (!this.head) {
            // The head and tail are the node
            this.head = this.tail = node;
        }

        // Otherwise the node needs to point to the current head
        node.next = this.head;
        // The previous first element needs to point at the prepended node
        this.head.prev = node;
        // The head needs to point at the prepended node
        this.head = node;

    }
}
```

## insertAt

We want to insert a node somewhere that is not at the beginning or the end of the linked list.

Let's look at the implementation of this:

```TypeScript

type Node<T> = {
    value: T;
    prev?: Node<T>;
    next?: Node<T>;
}

class DoublyLinkedList<T> {
    public length: number;
    private head?: Node<T>;
    private tail?: Node<T>;

    constructor() {
        this.length = 0;
        this.head = undefined;
        this.tail = undefined;
    }

    // ...
    insertAt(item: T, idx: number): void {
        // If we're trying to insert outside of the linked list throw an error
        if (idx > this.length) {
            throw new Error("Oh no");
        // If we're inserting at the end of the linked list use the append method
        } else if (idx === this.length) {
            this.append(item);
            return;
        // If we're inserting at the beginning of the linked list use the prepend method
        } else if (idx === 0) {
            this.prepend(item);
        }

        // As always when adding a node increment the length of the linked list
        this.length++;

        // Save the current head node as a variable
        let curr = this.head;
        // Walk through the linked list until we get to the index
        for (let i = 0; curr && i < idx; ++i) {
            // Increment the current node until we get to the index we want to insert at
            curr = curr.next;
        }

        // curr needs to be type Node<T>
        curr = curr as Node<T>;
        // Attach all the data to the Node to be inserted
        const node = { value: item } as Node<T>;

        // Point to the next node
        node.next = curr;
        // Point to the previous node
        node.prev = curr.prev;
        // Point the next node to our inserted node
        curr.prev = node;

        // If the current node has a previous node
        if (curr.prev) {
            // our current previous next node has to point to the current
            curr.prev.next = curr;
        }
    }
}
```

## Append

Append a node to the end of a linked list.

Let's look at the implementation:

```TypeScript
type Node<T> = {
    value: T;
    prev?: Node<T>;
    next?: Node<T>;
};

export default class DoublyLinkedList<T> {
    public length: number;
    private head?: Node<T>;
    private tail?: Node<T>;

    constructor() {
        this.length = 0;
        this.head = undefined;
    }

    // ...

    append(item: T): void {
        // Initialize the new node with it's data
        const node = { value: item } as Node<T>;

        // Increment the length of the linked list
        this.length++;

        // If there is no tail, i.e. there's nothing in the linked list
        if (!this.tail) {
            // Create the node where the head and tail point at the new node
            this.head = this.tail = node;
            return;
        }

        // Otherwise we need to take our tail and point to it
        node.prev = this.tail;
        // The tail needs to point to the node
        this.tail.next = node;
        // The tail now needs to point to our newly added node
        this.tail = node;
    }
}
```
