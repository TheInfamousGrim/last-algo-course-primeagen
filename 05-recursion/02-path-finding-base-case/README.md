# Path Finding: Base Case

We shall find the best path.

## Contents

1. [Maze Solver](#maze-solver)
2. [Base Case](#base-case)
3. [Recursion](#recursion)
4. [Putting It All Together](#putting-it-all-together)

## Maze Solver

How do we solve this?

```
[
    "# # # # # E #",
    "#           #",
    "# S # # # # #",
]
```

With recursion of course!

## Base Case

We need a solid base case in order to end the recursion or to continue recursing in another direction

Here are the base cases:

- It's a wall
- Off the map
- It's the end
- If we have seen it

Here's the solved code for the base cases:

```TypeScript
function walk(
    maze: string[],
    wall: string,
    curr: Point,
    end: Point,
    seen: boolean[][],
    path: Point[],
): boolean {
    // 1. base case
    // off the map
    if (
        curr.x < 0 ||
        curr.x >= maze[0].length ||
        curr.y < 0 ||
        curr.y >= maze.length
    ) {
        return false;
    }

    // On a wall
    if (maze[curr.y][curr.x] === wall) {
        return false;
    }

    // found the end
    if (curr.x === end.x && curr.y === end.y) {
        // If we've found the end we need to add that to our path
        path.push(end);
        return true;
    }
}

```

The base cases are super important as we need to know when to stop recursing and prevent a stack overflow.

## Recursion

Remember there are three steps that we need in order to recurse successfully:

1. pre
   - We need to add the current coordinates to our seen array
   - Then add the current coordinates to our path
2. recurse
   - We create a direction array made up of moving up, right, down, left
   - We loop through the direction array
   - get the current coordinates to move by from the direction array
   - Recursively call the walk function with the updated coodinates
   - If the walk recursive function returns true then we return true
3. post
   - If all of that has failed we pop the last coordinates from the current path
   - we return false

Let's look at that in code:

```TypeScript
const dir = [
    [-1, 0],
    [1, 0],
    [0, 1],
    [0, -1],
];

function walk(
    maze: string[],
    wall: string,
    curr: Point,
    end: Point,
    seen: boolean[][],
    path: Point[],
): boolean {
    // ...

    // Three steps to recursion
    // pre
    seen[curr.y][curr.x] = true;
    path.push(curr);

    // recurse
    for (let i = 0; i < dir.length; ++i) {
        const [x, y] = dir[i];
        if (
            walk(
                maze,
                wall,
                {
                    x: curr.x + x,
                    y: curr.y + y,
                },
                end,
                seen,
                path,
            )
        ) {
            return true;
        }
    }
    // post
    path.pop();

    return false;
}

```

## Putting it all together

Now that we've finished our recursive function let's put it all together and solve our maze:

```TypeScript
const dir = [
    [-1, 0],
    [1, 0],
    [0, 1],
    [0, -1],
];

function walk(
    maze: string[],
    wall: string,
    curr: Point,
    end: Point,
    seen: boolean[][],
    path: Point[],
): boolean {
    // 1. base case
    // off the map
    if (
        curr.x < 0 ||
        curr.x >= maze[0].length ||
        curr.y < 0 ||
        curr.y >= maze.length
    ) {
        return false;
    }

    // On a wall
    if (maze[curr.y][curr.x] === wall) {
        return false;
    }

    // found the end
    if (curr.x === end.x && curr.y === end.y) {
        path.push(end);
        return true;
    }

    // If we have seen it
    if (seen[curr.y][curr.x]) {
        return false;
    }

    // Three steps to recursion
    // pre
    seen[curr.y][curr.x] = true;
    path.push(curr);

    // recurse
    for (let i = 0; i < dir.length; ++i) {
        const [x, y] = dir[i];
        if (
            walk(
                maze,
                wall,
                {
                    x: curr.x + x,
                    y: curr.y + y,
                },
                end,
                seen,
                path,
            )
        ) {
            return true;
        }
    }
    // post
    path.pop();

    return false;
}

export default function solve(
    maze: string[],
    wall: string,
    start: Point,
    end: Point,
): Point[] {
    // We create an empty seen coordinates matrix
    const seen: boolean[][] = [];
    // We create our path array
    const path: Point[] = [];

    // Using the maze length we fill our seen matrix with false values
    for (let i = 0; i < maze.length; ++i) {
        seen.push(new Array(maze[0].length).fill(false));
    }

    // We call our recursive function to find our path to the end
    walk(maze, wall, start, end, seen, path);
    // We return our path
    return path;
}
```

## Time Complexity

O(N)
