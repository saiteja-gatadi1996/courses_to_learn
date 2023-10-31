- ## Queues

- Queue is a FIFO (First In First Out) data structure

- A queue is a linear collection where items are inserted at the end and are removed from the front. Hence queue is a FIFO (first-in first-out) data structure.

- Inserting into the queue is called Enqueue.
- Extracting from the queue is called Dequeue.
- Look at the top element in the queue (the one that will be removed on Dequeue). It is called Peek.

###### Ex: Queue is an abstraction of the behavior that is very common in our daily lives e.g. drive through of a Coffee Shop. It helps process requests or tasks in the order that they arrive.

![image](https://user-images.githubusercontent.com/42731246/164781709-cbf3d184-75f4-4129-88f6-c6dbc0b532d0.png)

![image](https://user-images.githubusercontent.com/42731246/164781730-4b6d469c-266e-442f-b76f-6709fd2915ce.png)

![image](https://user-images.githubusercontent.com/42731246/164781772-3cc1fe88-0c3c-4df5-a007-371fe31f44ee.png)

![image](https://user-images.githubusercontent.com/42731246/164781800-948a30b5-2f43-422c-a7cf-00645175e526.png)

![image](https://user-images.githubusercontent.com/42731246/164781836-3288b18b-903e-4c2f-9122-5341e164dee2.png)

---

### Queue Implementation

```js
function Queue() {
  this._head = 0
  this._data = [] //We are going to store the queue items in an array.
}
```

- data contains the items in the queue. At every enqueue, we push the new item into this array.
- head is the index of the top or head of the queue. At every dequeue, we return the element pointed by the head and then increment the head to point to the next item.

---

### Enqueue elements in the Queue

```js
Queue.prototype.enqueue = function (data) {
  this._data.push(data)
}
```

---

### Dequeue elements in the Queue

```js
Queue.prototype.dequeue = function () {
  if (this._head < 0 || this._head >= this._data.length) {
    return null
  }
  var dequeuedItem = this._data[this._head]
  this._head++

  return dequeuedItem
}
```

---

### Peek at the queue

```js
Queue.prototype.peek = function () {
  if (this._head < 0 || this._head >= this._data.length) {
    return null
  }
  return this._data[this._head]
}
```

---

### Queue in action

```js
var queue = new Queue()
console.log('Enqueue 100')
queue.enqueue(100)

console.log('Enqueue 200')
queue.enqueue(200)

console.log('Dequeue: ' + queue.dequeue())
console.log('Dequeue: ' + queue.dequeue())
console.log('Dequeue: ' + queue.dequeue())

//Output

// Enqueue 100
// Enqueue 200
// Dequeue: 100
// Dequeue: 200
// Dequeue: null
```

---

### Our dequeue implementation leaks memory

##### For learning purposes, we used a simpler version of Dequeue that leaks memory. Can you figure out how?

- When we dequeue, we never release the items from the array.
- With every dequeue, we move the head forward but the array still holds the reference to the item. It means, all the elements in the array at indexes less than the head are garbage.

- To fix this, we cleanup the array. We don't have to slow down each dequeue as deleting from the front of the array is a slow operation. We only do it after a certain threshold. e.g. we can say that we only cleaup the array when the garbage is 100 items.

```js
Queue.prototype.dequeue = function () {
  if (this._head < 0 || this._head >= this._data.length) {
    return null
  }

  var dequeuedItem = this._data[this._head]
  this._head++

  if (this._head === 100) {
    // We have 100 items in garbage
    // Remove items at indexes 0 to 99.
    this._data.splice(0, 100)

    // Reset the head
    this._head = 0
  }

  return dequeuedItem
}
```

---

### Does Javascript has built-in support for Queues

##### It does. Just like stacks, queues can be implemented using Javascript's array. Here's how.

- Enqueue can be implemented by using Array.push.

- Dequeue can be implemented by using Array.shift which removes the first element from the array.

- However, you can see that calling Shift at each dequeue is slow as it mutates the array. Hence, if you are writing performant code, the array we implemented is better as it has periodic/lazy cleanup instead of an aggressive cleanup.

---

### Summary

- A queue is a first-in-first-out (FIFO) data structure.
- It supports Enqueue for insertion and Dequeue for the extraction of items.
- Peek operation returns the topmost item in the queue.
- Javascript array supports Enqueue (Array.push) and Dequeue (Array.shift).
- Implementing dequeue using Array.shift can be slow.
- Dequeue operation should do periodic cleanup to save memory.
