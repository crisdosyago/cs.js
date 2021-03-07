# cs.js

Computer Science Data Structured and Algorithms in JavaScript ( Node.JS, ES ) in simple, clean, reusable code.

[cs101](https://npmjs.com/package/cs101) on NPM.

# Contents

## List Structures

- [x] [Singly-linked list](src/lib/singlist.js) - **O(1)** (access first or last) **O(n)** (insert, delete, update, find), **O(n)** space list
- [x] [Doubly-linked list](src/lib/linkedlist.js) - **O(1)** (reversal, access first or last) **O(n)** (insert, delete, update, find), **O(n)** space, traversable in forward or reverse list
- [x] [Self-organizing list](src/sol.js) **O(weird)** access-adapting (move to front or advance) list for faster access, good for cache and easy Least-Recently-Used eviction (pop off end)

## Tree Structures

- [x] [n-ary Tree](src/lib/tree.js) - any-arity tree structure, good as a basis for other tree structures and algorithms utilizing trees
- [x] [Heap](src/heap.js) - **O(1)** (find top) **O(log n)** (insert, delete, update), **O(n)** (heapify), **O(n)** space partially ordered stack of things, good for leaderboard
- [x] [Priority queue](src/pq.js) - **O(1)** (find top) **O(log n)** (insert, delete, update), **O(n)** (heapify), **O(n)** space stack of thing, priority pairs partially ordered by their priorities, good for job scheduling
- [x] [Trie](src/trie.js) - **O(k)** (insert, delete, update) **O(n)** trie-ify **O(n)** space tree of a list of sequences (commonly strings), good for full-text search

## Hybrid Tree/List Structures

- [x] [Skiplist](src/skiplist.js) - **O(log n)** (insert, delete, update, find (by key), find (by index)), **O(n log n)** skiplistify, **O(n) to O(n log n)** space **sorted** randomized list, with hybrid list/tree express lanes for fast access, very cool and efficient *rare O(n) worst case performance for insert, delete, update, find by key and find by index from bad random express-lane stops*, good for associative maps and anything really

## Seeking Algorithms

- [x] [BinarySearch](src/binarysearch.js) - **O(log n)** Find an item and its index in a sorted array, good for looking up books by title from an ordered list, or finding the slot to insert a new book
- [x] [QuickSelect](src/quickselect.js) - **O(N)** Find the nth-orderd item in an unordered array, good for "who came 1st (or k-th)" questions

## Sorting Algorithms 

- [x] [InsertionSort](src/insertionsort.js) - **O(n\*\*2)** (no binary search), **O(n log n)** (with binary search), **O(n)** (already sorted)
- [x] [MergeSort](src/mergesort.js) - **O(n log n)** (every case) **O(n) space** stable sort, divide and conquer, merging
- [x] [QuickSort](src/quicksort.js) - **O(n\*\*2)** (worst case of bad pivots) **O(n log n)** **O(1) space** non-stable in-place sort, divide and conquer, partitioning on pivot, *bad pivots can lead to quadratic performance.*

## Disclaimer

**DISCLAIMER: You will probably disagree with "simple", "clean", "reusable". I don't care what you think.** I'm OK you have your own view on it. Don't expect me to conform with yours, nor do I think there is :sparkles: *one true way* :sparkles: but I'm open to hear your open-minded suggestions of what you think works better, as long as you can respect that I'll have a different view maybe :smiley: and I don't think that makes either of us "right", nor do I think that either of us need to pretend the other is "wrong" if we disagree :heart: We can simply disagree :smiley:

## API Documentation

### Contents

  - [Singly-linked list](#singly-linked-list)
  - [Doubly-linked list](#doubly-linked-list)

------------

### Singly-linked list

Direct import:

```js
import SingList from './src/lib/singlist.js';
```

Package import:
```js
import CS from 'cs101';
const SingList = CS.SingList.Class
```

Creation:
```js
// empty singlist
const list = new SingList();

// filled singlist
const dataList = new SingList([1,2,3,4,5]);
```

Getting head:
```js
const list = new SingList(['beginning', 'middle', 'end']);

const thing = list.head.thing;

console.assert(thing === 'beginning');
```

Inserting at head:
```js
const list = new SingList(['x','y','z']);

list.head = new SingList.Node('w');

[...list]; // 'w', 'x', 'y', 'z'
```

Iterating:
```js
const list = new SingList([1,2,3,4,5]);

const things = [...list];

console.assert(things.join(',') === '1,2,3,4,5'); // true
```

Reversing:
```js
const list = new SingList([1,2,3,4,5]);

list.reverse();

const reversedThings = [...list];
console.assert([...list].join(',') === '5,4,3,2,1'); // true
```

### Doubly-linked list

Direct import:

```js
import LinkedList from './src/lib/linkedlist.js';
```

Direct import including Node class:

```js
import {Class as LinkedList, Node} from './src/lib/linkedlist.js';
```

Direct import including Node class alternative style:

```js
import LinkedList from './src/lib/linkedlist.js';
const Node = LinkedList.Node;
```

Package import:
```js
import CS from 'cs101';
const LinkedList = CS.LinkedList.Class
```

Creation:
```js
// empty linked list
const list = new LinkedList();

// filled linked list
const dataList = new LinkedList([1,2,3,4,5]);
```

Getting head:
```js
const list = new LinkedList(['beginning', 'middle', 'end']);

const thing = list.head.thing;

console.assert(thing === 'beginning');
```

Removing head:
```js
const headThing = list.shift();
```

Inserting at head (item only):

```js
list.unshift('i am a thing');
```

Inserting at head (using a Node):
```js
const list = new LinkedList(['x','y','z']);

list.head = new LinkedList.Node('w');

[...list]; // 'w', 'x', 'y', 'z'
```

Getting tail:
```js
const list = new LinkedList(['beginning', 'middle', 'end']);

const thing = list.tail.thing;

console.assert(thing === 'end');
```

Removing tail:
```js
const tailThing = list.pop();
```

Inserting at tail (item only):

```js
list.push('i am a thing');
```

Inserting at tail (using a Node):
```js
const list = new LinkedList(['x','y','z']);

list.tail = new LinkedList.Node('w');

[...list]; // 'w', 'x', 'y', 'z'
```

Iterating:
```js
const list = new LinkedList([1,2,3,4,5]);

const things = [...list].map(node => node.thing);

console.assert(things.join(',') === '1,2,3,4,5'); // true
```

Deleting a node:
```js
const list = new LinkedList([1,2,3,4,5]);

const node3 = [...list][2];

list.delete(node3);

const nodes = [...list].map(node => node.thing); // 1, 2, 4, 5
```

Deleting a node alternate style:
```js
const list = new LinkedList([1,2,3,4,5]);

const node3 = list.head.nextList(0).nextList(0);

list.delete(node3);

const nodes = [...list].map(node => node.thing); // 1, 2, 4, 5
```

Move a node toward head:
```js
const newTail = new LinkedList.Node('in the back');
list.tail = newTail;
list.advance(newTail);

console.assert([...list][list.length - 2] === newTail);
```

Reversing:
```js
const list = new LinkedList([1,2,3,4,5]);

list.reverse(); // O(1) operation

const reversedThings = [...list];
console.assert([...list].join(',') === '5,4,3,2,1'); // true
```


### Self-organizing list

### Heap

### Priority Queue

### Trie

### Skiplist

### Binary search

### Quick select

### Insertion sort

### Merge sort

### Quick sort


