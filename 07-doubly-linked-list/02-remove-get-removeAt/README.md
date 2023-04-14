# remove, get & removeAt

Getting and removing things from Linked Lists baby 😉

## Contents

1. [Remove](#remove)

## Remove

Removing an item from our linked list.

Let's look at an implementation:

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

    remove(item: T): T | undefined {
        // Let the current node be equal to the head
        let curr = this.head;

        // Walk through the linked list
        for (let i = 0; curr && i < this.length; ++i) {
            // If the current nodes value is equal to the items
            if (curr.value === item) {
                // Break as we've found the node to be removed
                break;
            }
            // Change the current node to the next node
            curr = curr.next;
        }

        // If there was no node found
        if (!curr) {
            // Return undefined
            return undefined;
        }

        // Otherwise remove the node
        return this.removeNode(curr);
    }

    // ...

    private removeNode(node: Node<T>): T | undefined {
        // Decrement the length of the linked list
        this.length--;

        // If the length of the linked list is 0 i.e. there's nothing in it
        if (this.length === 0) {
            //
            const out = this.head?.value;
            this.head = this.tail = undefined;
            return out;
        }

        // If there is a previous node
        if (node.prev) {
            // then the previous node's next node is equal to our removed node's next node
            node.prev.next = node.next;
        }
        // If there is a next node
        if (node.next) {
            // then the next node's previous node is equal to our removed node's previous node
            node.next.prev = node.prev;
        }
        // If the node to be removed is the head
        if (node === this.head) {
            // Then the head should point to the next node
            this.head = node.next;
        }
        // If the node is the tail
        if (node === this.tail) {
            // Then the tail should point to the previous node
            this.tail = node.prev;
        }

        // Then remove all the pointers for the node that is being removed
        node.prev = node.next = undefined;
        // Return the data that has been removed
        return node.value;
    }
}
```

## Get

Get ad node by it's index.

Let's look at an implementation:

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

    get(idx: number): T | undefined {
        // Return the node by it's index
        // Specifically return the data in that node
        return this.getAt(idx)?.value;
    }

    private getAt(idx: number) {
        // let the current node equal the head
        let curr = this.head;
        // Walk through the linked list
        for (let i = 0; curr && i < idx; ++i) {
            // increment the current node until we find the node we want
            curr = curr.next;
        }
        // Return the current node
        return curr;
    }
}
```

## removeAt

Remove a node at a specific index

Let's look at an implementation:

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

    removeAt(idx: number): T | undefined {
        // Get the node to removed from it's index
        const node = this.getAt(idx);

        // If there's no node
        if (!node) {
            // Return undefined
            return undefined;
        }

        // Otherwise return the data from the removed node
        return this.removeNode(node);
    }

    // ...

    private getAt(idx: number) {
        // let the current node equal the head
        let curr = this.head;
        // Walk through the linked list
        for (let i = 0; curr && i < idx; ++i) {
            // increment the current node until we find the node we want
            curr = curr.next;
        }
        // Return the current node
        return curr;
    }

    private removeNode(node: Node<T>): T | undefined {
        // Decrement the length of the linked list
        this.length--;

        // If the length of the linked list is 0 i.e. there's nothing in it
        if (this.length === 0) {
            //
            const out = this.head?.value;
            this.head = this.tail = undefined;
            return out;
        }

        // If there is a previous node
        if (node.prev) {
            // then the previous node's next node is equal to our removed node's next node
            node.prev.next = node.next;
        }
        // If there is a next node
        if (node.next) {
            // then the next node's previous node is equal to our removed node's previous node
            node.next.prev = node.prev;
        }
        // If the node to be removed is the head
        if (node === this.head) {
            // Then the head should point to the next node
            this.head = node.next;
        }
        // If the node is the tail
        if (node === this.tail) {
            // Then the tail should point to the previous node
            this.tail = node.prev;
        }

        // Then remove all the pointers for the node that is being removed
        node.prev = node.next = undefined;
        // Return the data that has been removed
        return node.value;
    }
}
```
