## Stacks

Stack is a Last In, First Out data structure useful is solving many problems in computer science. A stack is a list like data structure which allows three basic operations:

- Insert into the stack. This is known as Push.
- Extract the most recently added. This is called Pop.
- Look at the most recently added element without removing (popping) it. This is called Peek.

#### We always keep track of the topmost element in the stack

- ##### When we push an element, we update the top to start pointing to the newly added element.

![image](https://user-images.githubusercontent.com/42731246/164775898-2c2161d4-17b2-44c7-931c-c9c912501dc7.png)

---

![image](https://user-images.githubusercontent.com/42731246/164775967-7992cc06-40e5-4888-a861-1f148f02d955.png)

---

![image](https://user-images.githubusercontent.com/42731246/164776000-ed8ba93c-16c1-4a06-b421-677c2e2251d2.png)

---

- ##### When we pop an element, we update the top to point to the next most-recently-added element in the stack.

![image](https://user-images.githubusercontent.com/42731246/164776024-f8fe3cb1-06b8-47fd-9033-362dc238b01c.png)

---

![image](https://user-images.githubusercontent.com/42731246/164776049-57ced8f1-4ec8-42cb-9bc4-a47e4a8f14c2.png)

---

- ##### When we peek, we just return the data pointed by the top.

---

### Defining the stack

```js
// The  block of code below shows how a stack would be defined in JavaScript:

function Stack() {
  this._top = -1
  this._values = []
}
```

The Stack function would contain 2 parts:

- The index of the most recent element tracked by \_top. It is initialized by -1 to indicate that stack contains no elements.
- Array of values inserted into the stack tracked by \_values. It is initialized by an empty array.

---

### Pushing elements onto the stack

```js
// The block of code below defines how elements can be pushed or added to the stack.

Stack.prototype.push = function (data) {
  this._top++
  this._values[this._top] = data
}

//We just increment the top to get the index for new element and then insert the data. Top is automatically pointing to the top-most element in the stack.
```

---

### Popping elements from the stack

- First, we check that stack has any element.

- If the stack is empty, we return null.

- We then note down the element at the top, then reduce the top and reduce the size of the array.

- As the last step, we return the element that was at the top.

```js
Stack.prototype.pop = function () {
  if (this._top < 0) {
    return null
  }

  var topElement = this._values[this._top]
  this._top--
  this._values.length--

  return topElement
}
```

---

### Peeking at the top element

```js
Stack.prototype.peek = function () {
  if (this._top < 0) {
    return null
  }
  return this._values[this._top]
}
```

---

### Stack in action

```js
var stack = new Stack()

for (var i = 100; i <= 300; i += 100) {
  console.log('Pushing on stack: ' + i)
  stack.push(i)
}

console.log('Top of the stack using Peek: ' + stack.peek())
console.log('Pop from stack. Popped element = ' + stack.pop())
console.log('Pop from stack. Popped element = ' + stack.pop())

// Output

Pushing on stack: 100
Pushing on stack: 200
Pushing on stack: 300
Top of the stack using Peek: 300
Pop from stack. Popped element = 300
Pop from stack. Popped element = 200


```

---

### Exercises:

##### Let's implement a method 'size' that returns the number of elements in the stack.

```js
Stack.prototype.size = function () {
  return this._values.length
}
```

---

##### Let's implement 'isEmpty' method. It returns true when the stack is empty and returns false when the stack has one or more elements

```js
Stack.prototype.isEmpty = function () {
  // Return true when empty //
  if (this._values <= 0) {
    return true
  }
  // Return false when not empty
  if (this._values > 0) {
    return false
  }
}
```

---

### Does Javascript has a built-in Stack?

```js
// Yes. In fact, the Array in Javascript acts as a stack and already has the appropriate methods to use it like a stack. Look at the  code below:

var stack = []
console.log('Push 100 in stack')
stack.push(100)
console.log('Popped from Stack: ' + stack.pop())

// Output
Push 100 in stack
Popped from Stack: 100
```

---

### Summary

- Stack is a LIFO data structure.
- Stack has 3 basic operations: Push, Pop and Peek.
- Javascript Array is actually a stack and supports Push and Pop.
