# cs.js

Computer Science Data Structured and Algorithms in JavaScript ( Node.JS, ES ) in simple, clean, reusable code.

[cs101](https://npmjs.com/package/cs101) on NPM.

# Contents

Click links below to go *straight to the code* :sparkles: for each structure or algorithm;

Or [jump straight to the API documentation](#api-documentation).

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
  - [Self-organizing list](#self-organizing-list)
  - [Heap](#heap)
  - [Priority queue](#priority-queue)
  - [Trie](#trie)
  - [Skiplist](#skiplist)
  - [Binary search](#binary-search)

------------

### Singly-linked list

  *Note: there is no cycle checking, and it's possible to create cycles by adding nodes to head that are already present in the list.*

  Direct import:

  ```js
  import SingList from './src/lib/singlist.js';
  ```

  Package import:
  ```js
  import * as CS from 'cs101';
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
  console.assert(reversedThings.join(',') === '5,4,3,2,1'); // true
  ```

### Doubly-linked list

  *Note: there is no cycle checking, and it's possible to create cycles by adding nodes that are already present in the list.*

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
  import * as CS from 'cs101';
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

  const reversedThings = [...list].map(({thing}) => thing);
  console.assert(reversedThings.join(',') === '5,4,3,2,1'); // true
  ```

  Get length:
  ```js
  list.length; // 5
  ```

### Self-organizing list

  Importing directly:
  ```js
    import SOL from './src/sol.js';
  ```

  Importing from package:
  ```js
    import * as CS from 'cs101';
    const SOL = CS.SOL.Class;
  ```

  Creating:
  ```js
    const sol = new SOL({
      asLinkedList: false,        /* underlying store is linked list, false is array */
      moveToFront: 0.8,           /* MTF reorganize scheme probability */
      swap: 0.2,                  /* swap reorganize scheme probability */
      dupesOK: false,             /* duplicate keys are not OK, true they are */
    });
  ```

  Setting a key, value pair:
  ```js
  sol.set('taco', {awesome:true});
  ```

  Testing membership:
  ```js
  sol.has('taco'); // true
  ```

  Getting a value from a key:
  ```js
  sol.get('taco'); // {index: 0, copy: {key: 'taco', value: {awesome:true}}} 
  ```

  Deleting a key:
  ```js
  sol.delete('taco'); // :'(
  sol.get('taco'); // {index: undefined, copy: undefined}
  ```

  Iterating:
  ```js
  sol.set('taco', {trulyAwesome:[true, true]}); // XD
  [...sol]; // [ {key: 'taco', value: {trulyAwesome: [true, true]}} ]
  ```

  Get length:
  ```js
  sol.length; // 1
  ```

### Heap

  Importing directly:
  ```js
  import Heap from './src/heap.js';
  ```

  Importing from package:
  ```js
  import * as CS from 'cs101';
  const Heap = CS.Heap.Class;
  ```

  Creating:
  ```js
  const data = [0,10,8,7,2,1];
  const heap = new Heap({
    asTree: false,          /* underlying implementation as tree, false is list implementation */
    max: true,              /* max heap, false is min heap */
    arity: 2,               /* binary, then 3 is ternary, etc. */
    compare: undefined      /* a custom comparator per JS Array.sort compareFunction interface */
      // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#parameters 
      // with comparison directed by the heap property
      // so compare(bigger, smaller) is > 0 for max heap
      // while compare(smaller, bigger) is > 0 for min heap
      // and vice versa
      // in essence, it's 
      // compare(top, bottom) > 0 and compare(bottom, top) < 0
      // DEFAULT comparison is simply this applied to Numbers
  }, data); // O(n) (uses Floyd's heapify)
  ```

  Getting size:
  ```js
  heap.size; // 6
  ```

  Getting top:
  ```js
  heap.peek(); // 10 O(1)
  ```

  Replacing top:
  ```js
  heap.replace(22); // 10 O(log n)
  heap.size; // 6
  ```

  Removing top:
  ```js
  heap.pop(); // 22 O(log n)
  heap.size; // 5
  heap.peek(); // 8
  ```

  Pushing something on:
  ```js
  heap.push(-5); 
  heap.peek(); // 8
  heap.push(9);
  heap.peek(); // 9
  ```

### Priority Queue

  Importing directly:
  ```js
  import PQ from './src/pq.js';
  ```

  Importing from package:
  ```js
  import * as CS from 'cs101';
  const PQ = CS.PQ.Class;
  ```

  Creating:
  ```js
  // data should have priority
  const data = [
    {
      priority: 8,
      stuff: 'ooo',
      moreStuff: {ok: true}
    },
    { 
      priority: 2,
      hello: 1
    },
    {
      priority: 9,
      text: 'yes'
    }
  ];

  // default options shown below
  const pq = new PQ({
    max: true,
    compare: function (A, B) {
      const {priority:pA = Empty} = A;
      const {priority:pB = Empty} = B;

      if ( pB == Empty ) {
        return 1;
      } else if ( pA == Empty ) {
        return -1;
      }

      if ( pA > pB ) {
        return this.config.max ? 1 : -1;
      } else if ( pA == pB ) {
        return 0;
      } else {
        return !this.config.max ? 1 : -1;
      }
    }
  }, data); // O(n) (uses Floyd's heapify)
  ```

  Get size:
  ```js
  pq.size;  // 3
  ```

  Get top priority:
  ```js
  pq.top(); // {priority: 9, text: 'yes'}
  ```

  Remove top priority:
  ```js
  pq.pull(); // {priority: 9, text: 'yes'}
  pq.top(); // {priority: 8, stuff: 'ooo', moreStuff: {ok: true}}
  pq.size; // 2
  ```

### Trie

  Importing directly:
  ```js
  import Trie from './src/trie.js';
  ```

  Importing from package:
  ```js
  import * as CS from 'cs101';
  const Trie = CS.Trie.Class;
  ```

  Creating (strings only, Map or object):
  ```js
  const data1 = ['abc', 'def'];
  const trie1 = new Trie({
    asTree: false,          /* underlying implementation as tree, false is list implementation */
    max: true,              /* max heap, false is min heap */
    arity: 2,               /* binary, then 3 is ternary, etc. */
    compare: undefined      /* a custom comparator per JS Array.sort compareFunction interface */
      // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#parameters 
      // with comparison directed by the heap property
      // so compare(bigger, smaller) is > 0 for max heap
      // while compare(smaller, bigger) is > 0 for min heap
      // and vice versa
      // in essence, it's 
      // compare(top, bottom) > 0 and compare(bottom, top) < 0
      // DEFAULT comparison is simply this applied to Numbers
  }, data); // O(n) (uses Floyd's heapify)

  const data2 = new Map([
    ['abc', {movie: 'ok'}],
    ['def', {time: 'yes'}]
  ]);
  const trie2 = new Trie(null, data);

  const data3 = {
    abc: {movie: 'ok'},
    def: {time: 'yes'},
  }
  const trie3 = new Trie(null, data);
  ```

  Getting size:
  ```js
  trie1.size; // 2
  trie2.size; // 2
  trie3.size; // 2
  ```

  Membership:
  ```js
  trie1.has('ab'); // no
  trie1.has('abc'); // yes
  trie1.has('xyz'); // no
  ```

  Setting / updating:
  ```js
  trie1.set('xyz', {everybody: 'else'});
  trie1.set('zzz', {accounting: true});
  trie1.size; // 3
  ```

  Getting:
  ```js
  trie1.get('zzz'); // {found: true, value: {accounting: true}}
  trie1.get('---'); // {found: false, value: undefined}
  ```

  Deleting:
  ```js
  trie1.delete('def');
  trie1.size; // 2
  ```

  Iterating (keys, values, entries):
  ```js
    [...trie1.keys()]; // 'abc', 'zzz', 
    [...trie1.values()]; // true, {accounting: true}
    [...trie1.entries()]; // ['abc', true], ['zzz', {accounting:true}
  ```

### Skiplist

  Importing directly:
  ```js
  import SkipList from './src/skiplist.js';
  ```

  Importing from package:
  ```js
  import * as CS from 'cs101';
  const SkipList = CS.SkipList.Class;
  ```

  Creating:
  ```js
  const data = [1,2,3,4,5]; // data can also be empty or undefined is OK

  // default options shown below
  const skiplist = new SkipList({
    max: false,               /* increasing order, true gives decreasing order */
    p: 1/2,                   /* probability node lifts to higher levels */
    randomized: true,         /* if we base lifting on randomizedation   */
      // false uses a determ  inistic lifting scheme
    duplicatesOkay: false,    /* only insert each thing once, true allows dupes */
    compare: undefined,       /* custom comparator function */
  }, data); // O(n log(1/p) n)
  ```

  Get size:
  ```js
  skiplist.size;  // 3
  ```

  Set thing:
  ```js
  skiplist.insert(84, '1984'); //
  skiplist.set(84, '1984'); // alias of insert
  skiplist.size; // 6 (would be 7 if dupesOK: true)
  ```

  Get thing:
  ```js
  skiplist.get(84); // {has: true, value: '1984', index: 5}
  ```

  Get thing by index:
  ```js
  skiplist.getSlot(5); // {has: true, thing: 84, value: '1984'}
  skiplist.getSlot(0); // {has: true, thing: 1, value: true}
  ```

  Delete thing:
  ```js
  skiplist.delete(2); // true
  skiplist.delete('foo'); // false
  skiplist.size; // 5
  skiplist.getSlot(5); // {has: false, thing: undefined, value: undefined}
  skiplist.getSlot(4); // {has: true, thing: 84, value: '1984'}
  ```

  Membership:

  ```js
  skiplist.has(84); // true;
  skiplist.has('bar'); // false;
  ```

  Iteration (keys, values, entries):
  ```js
  [...skiplist.keys()]; // 1, 3, 4, 5, 84
  [...skiplist.values()]; // true, true, true, true, '1984'
  [...skiplist.entries()]; // [1, true], [3, true], [4, true], [5, true], [84, '1984']
  ```

### Binary search

  Import direct:
  ```js
    import BinarySearch from './src/binarysearch.js';
    // equivalent
    import {find} from './src/binarysearch.js';
    // lower-level alternatives
    import {iterativeBinarySearch} from './src/binarysearch.js';
    import {recursiveBinarySearch} from './src/binarysearch.js';
  ```

  Import from package:
  ```js
    import * as CS from 'cs101';
    const BinarySearch = CS.BinarySearch.find;
  ```

  Finding an item:
  ```js
  const list = ['92', 'abc', 'delta', 'twenty1'];
  const {has, index} = BinarySearch(list, 'abc'); // {has: true, index: 1}
  ```

  Finding where to insert an item:
  ```js
  // index gives where to insert before (so insert at 3, moves existing list[3] to list[4])
  const {has, index} = BinarySearch(list, 'really'); // {has: false, index: 3}
  list.splice(index, 0, 'really');
  ```

  Using more options:

  ```js
  const list = [{a:1,b:'hi'}, {a:2,b:'9'},{a:4,b:'12321'}];
  const {has, index} = BinarySearch(list, {a:2}, {
    compare: ({a:a1}, {a:a2}) => Math.sign(a1-a2),
    recursive: true               /* false is iterative, the default */
  }); // {has: true, index: 1}
  ```

  Using iterative and recursive directly:
  ```js
  import {iterativeBinarySearch} from './src/binarysearch.js';
  import {recursiveBinarySearch} from './src/binarysearch.js';

  const list = [1,2,3,4,5,8, 7,4,3,2,1];
  // args are -> (data, item, low, high, opts)
  iterativeBinarySearch(list, 4, 0, 6, {compare:(a,b) => Math.sign(a-b)}); // {has: true, index: 3}
  recursiveBinarySearch(list, 4, 0, 6, {compare:(a,b) => Math.sign(a-b)}); // {has: true, index: 3}
  ```

### Quick select

### Insertion sort

### Merge sort

### Quick sort


