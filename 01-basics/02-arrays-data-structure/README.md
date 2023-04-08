# Arrays Data Structure

This will shockingly be a data structure you know!!!!

## Contents

1. [What is An Array?](#what-is-an-array)

## What is An Array?

If const a = [] isn't an array, what is it?

- A contiguous memory space
- Getting an array at a specific index
  - Each index will take the width of the type (8bit, 16bit, 32bit etc.)
  - Multiply at the offset (index 0, 1, 2, 3 etc)
  - Grab the data that specific offset
  - O(1)
- Insertion at a specific index
  - When you insert something, it's generally overwriting something
  - You go to the specific address of the index and add the width of the type
  - Multiply by the offset and then you can add it in
  - O(1)
- Deletion at a specific index
  - Deletion isn't technically yeeting something out of existence
  - You can set it to zero or null
  - Works in the same way
  - Multiply the offset(index) by the width of the type
  - O(1)

### Some More Array Info

They are fixed size, contiguous memory chunks.

- That means you cannot grow it
- There is no "insertAt" or push or pop. Doesn't mean you can't write those though.
