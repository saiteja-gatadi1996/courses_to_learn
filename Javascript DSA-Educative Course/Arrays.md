## Arrays

- One unique thing about Javascript arrays is that they are actually objects and indices are just property names in that object. Indices are usually numbers and so Javascript arrays convert these numerical indices to string keys and then assign them as object properties. Therefore, if you access array[0], you are actually accessing the property "0" of the object array.

```js
// Here's how we can create an array in javascript.
var topics = []
```

```js
// Initiliazing an array
var primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
```

```js
///sample program
var topics = []
console.log('[' + topics + '] has length = ' + topics.length) // [] has length = 0

topics.push('Arrays')
topics.push('Stacks')
topics.push('Queues')

console.log('[' + topics + '] has length = ' + topics.length) //[Arrays,Stacks,Queues] has length = 3
```

```js
// Array elements are accessed using the indices ranging from 0 to 'length-1'.

var topics = []

topics.push('Arrays')
topics.push('Stacks')
topics.push('Queues')

for (var i = 0; i < topics.length; i++) {
  console.log(topics[i])
}

// Output

Arrays
Stacks
Queues
```

###### The 'new' Array Syntax

- Arrays can also be created with the new keyword in JavaScript as array is an object. In most cases, this way of creating arrays is inefficient and should be avoided. However, for learning, here's the syntax.

```js
var topics = new Array('Arrays', 'Stacks', 'Quotes')
```

```js
// Removing elements from an array

var tutorials = ['Arrays', 'Stacks', 'Queues']
console.log('Before Splice: ' + tutorials) //Before Splice: Arrays,Stacks,Queues
tutorials.splice(1, 1)
console.log('After Splice: ' + tutorials) //After Splice: Arrays,Queues
```