## Linked Lists

Linked lists are are an ordered set of nodes where each node contains a link to its successor.

- A linked list is a data structure that holds a sequence of linked nodes. Each node contains data and a reference, where reference points to its successor node in the Linked List.

![image](https://user-images.githubusercontent.com/42731246/164888960-c8ea1d6d-99a4-4cbf-ad4f-3453344b6539.png)

- The above diagram shows a typical example of a singly linked list. It consists of 3 nodes. The first node consists of a value of 1 and contains a pointer to the next node. The next node in the list has a value of 2 and subsequently consists of a reference to the last node in the list and so on. The last node in a linked list contains a value 3 but it doesn't point to anything.

- When a reference doesn't point to any valid object, programming languages typically have a "NULL" value to represent the missing value. In Javascript, we use "null" for that purpose - and it's called a null reference.

```js
Reference is also sometimes called a pointer. This comes from the C/C++ world where variables can point to memory addresses.

In Javascript, we cannot point to memory addresses. Instead we have references to objects.
```

- The first node in the linked list is called Head Node. Head node is our handle to the linked list. We traverse the linked list starting at the head node and then move to the node pointed by the current node.

---

### Why another 'List' when we already have an array?

- We already have a built-in type Array that acts as a container similar to a linked list. Turns out that array is not an efficient data structure in all cases. Arrays are implemented in programming languages in a certain way which makes it very efficient for certain cases while they are highly inefficient for other cases.

- Given how arrays are stored in memory, it is usually inefficient to insert elements in the middle.

- However, linked list also has drawbacks. You cannot access an element randomly and have to traverse from the first node to the next and so on until you find your desired node.

- ###### If you need to access elements at random positions in the list, don't use a Linked List.

---

### The Node element in JavaScript

```js
var node = {
  data: 0, // some data value
  next: null, // reference to next node
}
```

---

### Manually Build a Linked List

```js
var firstNode = {
  data: 100,
  next: null,
}

var secondNode = {
  data: 200,
  next: null,
}

var thirdNode = {
  data: 300,
  next: null,
}

firstNode.next = secondNode
secondNode.next = thirdNode

var currentNode = firstNode

// Iterate over the Linked List and print nodes
while (currentNode != null) {
  console.log('Node value: ' + currentNode.data)
  currentNode = currentNode.next
}

// Output:
Node value: 100
Node value: 200
Node value: 300
```

---

### Steps to be follwed to create the linked list

![image](https://user-images.githubusercontent.com/42731246/164889452-e17f57f0-758a-4a5b-a005-9fc79526f680.png)

![image](https://user-images.githubusercontent.com/42731246/164889466-7f26d81c-c056-4837-b31a-fe6265e61ac0.png)

![image](https://user-images.githubusercontent.com/42731246/164889467-410a5ea3-4924-4fec-b4c5-e24ce4fb4c44.png)

---

### Generalizing Linked List Operations

- It's obvious from the above code that if we wanted to create multiple nodes, we will have to write the same lines of code over and over again (to iterate over the linked list, find the last element and extend the linked list by adding a new node).

- Instead, we will create a LinkedList class that provides such functions over the linked list.

```js
function Node(data) {
  this.data = data;
  this.next = null;
}

function LinkedList() {
  this._length = 0;
  this._head = null;
}

LinkedList.prototype.push = function(data) {
  // Create a new node with Data
  var node = new Node(data);

  // We are inserting the first node in the list
  if (this._head === null) {
    this._head = node;
  } else {
    // Find the last node
    var current = this._head;

    while (current.next) {
      current = current.next;
    }

    current.next = node;
  }

  // Increment the length
  this._length++;
}

// We follow the 0 based indexes just like Arrays
LinkedList.prototype.itemAt = function(index) {
  // Ensure that the index is within bounds
  if (index < 0 || index >= this._length) {
	// Return Null when index is out of bounds
	return null;
  }

  var current = this._head;
  var counter = 0;

  while (counter < index) {
    current = current.next;
    counter++;
  }

  return current.data;
}

// Returns Size of Current Linked List
LinkedList.prototype.size = function() {
  return this._length;
}

// Let's create a Linked List and add 3 nodes
var list = new LinkedList();
list.push(100);
list.push(200);
list.push(300);

for (i = 0; i < list.size(); i++) {
  console.log("Node value: " + list.itemAt(i));
}

// Output:

Node value: 100
Node value: 200
Node value: 300
```

![image](https://user-images.githubusercontent.com/42731246/164894693-f94f3351-1f45-49d8-9e9f-6d376e2bd5bf.png)

![image](https://user-images.githubusercontent.com/42731246/164894698-c278e366-286a-4a63-a1bd-54059dc7780c.png)

![image](https://user-images.githubusercontent.com/42731246/164894707-1ed916e3-1b59-45b1-a500-7bb7c02c4cb1.png)

![image](https://user-images.githubusercontent.com/42731246/164894713-a37c370f-52ac-493b-ae5a-cfd3a09a4908.png)

---

### Understanding the above code

- The first section of code created our Node class. The function takes the data value, assigns it to the node via the 'this' attribute. Initially, the function will cause the node to point to nothing because at this point in time we don't know where the node needs to be inserted in the linked list.

```js
function Node(data) {
  this.data = data
  this.next = null
}
```

- Next we defined our linked list. The linked list will initially have a length of 0 and the first element or the head element will point to nothing. Simple enough.

```js
function LinkedList() {
  this._length = 0
  this._head = null
}
```

##### Next we add a push function to our linked list class. This function will be used to append nodes to the linked list. There are two cases while appending a node to the linked list.

- If the linked list is empty, then we are inserting the first node. This node will become the head node.
- Linked List already has one or more nodes. In this case, node will be inserted at the tail of the linked list.

##### We create the node and then insert the node at the right position. Note how we traverse to the last element in the linked list. We have a temporary variable called current which is updated in the loop to the next element in the list. When current.next becomes null, it means that we have reached the end of the list. Here, the while loop will terminate. We point the next of the last node to the newly created node. As the last step, we increment the size of the linked list.

```js
LinkedList.prototype.push = function (data) {
  // Create a new node with Data
  var node = new Node(data)

  // We are inserting the first node in the list
  if (this._head === null) {
    this._head = node
  } else {
    // Find the last node
    var current = this._head

    while (current.next) {
      current = current.next
    }

    current.next = node
  }

  // Increment the length
  this._length++
}
```

##### Similar to the push method, we introduced itemAt method. This method retrieves and returns the value of node at the given index. It's similar to array's lookup method. As the first step, we ensure that the Linked List has enough elements. If index is too low (less than 0) or too high (greater than the length), we simply return null.

- We could have considered throwing an exception here as well (many programming languages throw OutOfBoundException is such cases).

- Now, if the linked list has enough items, we traverse to the desired index, starting from the head node. Remember what we discussed in the beginning as a LinkedList v.s. Array tradeoff. In Array, we could have randomly accessed a given index. Here, we have to iterate through the linked list in a serial order until we get to the desired node. Once we are at the node, we return the data contained by that node.

```js
// We follow the 0 based indexes just like Arrays
LinkedList.prototype.itemAt = function (index) {
  // Ensure that the index is within bounds
  if (index < 0 || index >= this._length) {
    // Return Null when index is out of bounds
    return null
  }

  var current = this._head
  var counter = 0

  while (counter < index) {
    current = current.next
    counter++
  }

  return current.data
}
```

---

### Note:

```js
//This is a special case condition if the node to be inserted is the first node in the linked list.
if (this._head === null) {
  this._head = node
}
```

## Removing a Node from the Linked List

- Our remove function will take the index of the element to be removed. If the node to be removed happens to be the head node, it will update the head node as well.

```js
// Removes the element and returns the data
// in the node that was removed
LinkedList.prototype.remove = function (index) {
  // Ensure that the index is within bounds
  if (index < 0 || index >= this._length) {
    return null
  }

  var current = this._head

  if (index === 0) {
    // Special case for removing the head node.
    this._head = current.next
  } else {
    // Track previous element
    var previous = null
    var counter = 0

    while (counter < index) {
      previous = current
      current = current.next
      counter++
    }

    // Set previous node's next
    // to the node after the deleted node
    previous.next = current.next
  }

  this._length--
  return current.data
}

// Let's create a Linked List and add 3 nodes
var list = new LinkedList()
list.push('Stacks')
list.push('Queues')
list.push('Arrays')
list.push('Sets')

console.log('Length before removal: ' + list.size())

// Remove the 3rd element
var removed = list.remove(2)
console.log('removed: ' + removed)

// Remove the head node
var removed = list.remove(0)
console.log('removed: ' + removed)

console.log('Length after removal: ' + list.size())

// Output:
Length before removal: 4
removed: Arrays
removed: Stacks
Length after removal: 2
```
![image](https://user-images.githubusercontent.com/42731246/164896335-b8a7fa00-c8a9-4d4c-ba5b-7f357361d047.png)

![image](https://user-images.githubusercontent.com/42731246/164896339-dcb5e7e8-2e45-4df4-b1d1-0acc19b2e5a7.png)

![image](https://user-images.githubusercontent.com/42731246/164896344-ed161bd7-d3ab-4262-86fe-66fd807e0cf1.png)

##### Let's go through the deletion code
- We start at the head and traverse to the node to be deleted. If the node to be deleted is the head, then we just point the _head to the second node in the list (which could be null if it's a single node linked list). 

- If the node to be deleted is not the head, then we traverse to the node that is going to be deleted. While traversing to the node, we keep track of the previous node as well. Why? Because in a singly linked list, there is no way to access the previous node of a given node. Hence, we need to explicitly track the previous node as we traverse. Once we reach the desired node, we connect the previous node's next to current node's next. Think of it as if the current node was a middleman and now previous node is making a direct connection to the node after the current node (or metaphorically speaking, we are removing the middleman). 

After setting the references, we then reduce the length and return the data in the current node.

## Summary
- Linked list comprises of a chain of nodes.
- Each node contains a data element and the reference to the next node in the chain.
- Linked lists are better for scenarios where you need to insert or remove elements from the middle.
- Unlike arrays, linked lists don't provide random access. Hence, look up and retrieval in linked lists are slower than an array.