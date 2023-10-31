## Sets

- A set is an unordered collection of related members in which no member occurs more than once.
- A set that doesnt contain any element is often called null set.

![image](https://user-images.githubusercontent.com/42731246/164887295-c1ba1f1d-ceb4-4fcc-9271-2ffeba8dac7a.png)

The most common set operations are given below:

- Union - This is wherein a new set is constructed by combining the members of one set with the members of another set.

- Intersection - This is wherein a new set is constructed by adding all the members of one set that also exist in a second set.

- Difference - This is wherein a new set is constructed by adding all the members of one set except those that also exist in a second set.

### Set Representation in JavaScript

- The set is represented as an Object and the values of the set can be inserted as properties. The size is maintained separately using a size variable. There are other ways of implementing sets in JavaScript. We have picked Object for its simplicity.

```js
function Set() {
  this.set = {}
  this.size = 0
}
```

### Adding items to the set

- The first check is done to see if the data actually exists in our set. This is done by using the hasOwnProperty method which is available for JavaScript objects.
- If not, then the data value is added to the set by setting the property of the object to the data which is passed to the add function. The associated value is set to true, just to indicate that the property is part of the set. Technically in this implementation of a set, the value can be set to anything.

```js
Set.prototype.add = function (data) {
  if (!this.set.hasOwnProperty(data)) {
    this.set[data] = 'true'
    this.size++
  }
}
```

### Removing an item from the set

- First we ensure that the data value to be removed is available in the set. This is done by using the hasOwnProperty function of JavaScript objects.
- If the property does exist , then it is removed from the set data structure.
- At the same time, the size value is decremented to indicate that an element has been removed from the set.

```js
Set.prototype.remove = function (data) {
  if (this.set.hasOwnProperty(data)) {
    delete this.set[data]
    this.size--
  }
}
```

```js
var myset = new Set();
myset.add(1);
myset.add(2);
myset.add(3);
myset.print();
console.log('removing 2');
myset.remove(2);
myset.print();

O/P:
{1, 2, 3}
removing 2
{1, 3}
```

### Membership in the set

One of the key functionalities of sets is the determnation of whether a value actually beongs to a set. The following code snippet shows how this can be accomplished:

```js
Set.prototype.member = function (data) {
  if (this.set.hasOwnProperty(data)) {
    return true
  } else {
    return false
  }
}
```

#### let's implement a method size that returns the number of items in set.

```js
Set.prototype.sizeOfSet = function (data) {
  return this.size
}
```

### Union of two sets

- The union of two sets returns a set containing all elements in either this or the other set

```js
Set.prototype.union = function (secondSet) {
  var unionSet = new Set()
  for (var key in this.set) {
    if (this.set.hasOwnProperty(key)) {
      unionSet.add(key)
    }
  }
  for (var key in secondSet.set) {
    if (!unionSet.set.hasOwnProperty(key)) {
      unionSet.add(key)
    }
  }
  return unionSet
}
```

### Intersection of two sets

- The intersection of two sets returns a set containing all elements that exist in both sets. Here goes the implementation for intersection for our set data structure:

```js
Set.prototype.intersect = function (secondSet) {
  var inter = new Set()
  for (var key in this.set) {
    if (secondSet.set.hasOwnProperty(key)) {
      inter.add(key)
    }
  }
  return inter
}
```

---

#### ES6 has a built-in Set object. It is implemented now in some browsers and in near future will get full support. We recommend that instead of implementing your own Set structure leverage the one thats provided by ES6. A key advantage of this Set Object is that it doesn't coerce all keys to a string like the Object does so you can have both 6 and "6" as separate keys.

---

### Summary

A set is a data structure which has the following key properties:

- Elements are unordered.
- No Duplicates are present.
- The add and remove functions are used to add and remove items from the set.
- The union of two sets returns a set containing all elements in either this or the other set.
- The intersection of two sets returns a set containing all elements in both this and the other set.
