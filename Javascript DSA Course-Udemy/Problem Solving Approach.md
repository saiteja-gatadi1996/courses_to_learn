## ALGORITHM

![image](https://user-images.githubusercontent.com/42731246/184505170-b9f95181-b356-42b5-ae18-7373d324a06b.png)

---

### Understand

![image](https://user-images.githubusercontent.com/42731246/184506413-d524796a-51d0-4e7d-a3a5-b6b97e389379.png)

![image](https://user-images.githubusercontent.com/42731246/184506436-2c11dd9e-f197-4df7-bad3-91f93e96f50d.png)

---

![image](https://user-images.githubusercontent.com/42731246/184506671-9f1b507e-b442-4925-a500-b1c4f90f475e.png)

---

#### Comparing the below code with exploring all the above examples

![image](https://user-images.githubusercontent.com/42731246/184506689-6886c8ba-6a7e-4592-a091-45bee5ff5c65.png)

### Simple Example

- #### Should it just return the letters that are in there? What about the letters that aren't there?

### Complex Example

- #### What about if somebody provides like "my phone number is 182763"

- #### So if this was an input, what would we expect to return? Do we want to account for spaces? That's an important one. What about other characters? Dollar signs underscores numbers. That's a big one. Are we going to put numbers in there? And an even more important one that definitely would come up.

- #### What if we have Uppercase letters like ("Hello hi")

- #### Are there do we store an uppercase H and a lowercase h? Do we ignore casing? Should our object have H uppercase one, h lowercase one or just h two?

### Explore Examples with empty inputs

- #### What if we pass empty string input, Do we want to return an empty object at the end? Do we want to return null or false or undefined or maybe an error?

### Explore Examples with Invalid inputs

- #### So what if somebody passes in something that isn't a string? They pass in a number or they pass in an object or they pass in null.

---

### Break it Down

![image](https://user-images.githubusercontent.com/42731246/184507032-39e254c6-b90f-42ca-a13e-ca49576f9bd1.png)

---

![image](https://user-images.githubusercontent.com/42731246/184507204-102b3b1b-be00-4dcb-845d-e4f1af7599a7.png)

---

### Solve/Simplify the Problem with/without hints

```js
function charCount(str) {
  const result = {}
  for (var i = 0; i < str.length; i++) {
    const char = str[i].toLowerCase()
    if (/[a-z0-9]/.test(char)) {
      if (result[char] > 0) {
        result[char]++
      } else {
        result[char] = 1
      }
    }
  }
  return result
}

charCount('Hello hi!')
```

### Refactor

![image](https://user-images.githubusercontent.com/42731246/184549131-bfdd16bd-fed0-40f4-ae58-a88197328805.png)

---

```js
function charCount(str) {
  const result = {}
  for (let char of str) {
    if (isAlphaNumeric(char)) {
      char = char.toLowerCase()
      result[char] = ++result[char] || 1
    }
  }
  return result
}

function isAlphaNumeric(char) {
  const code = char.charCodeAt(0)
  if (
    !(code > 47 && code < 58) && //numeric (0-9)
    !(code > 64 && code < 91) && // upper aplha (A-Z)
    !(code > 96 && code < 123) //lower alpha (a-z)
  ) {
    return false
  }
  return true
}

charCount('Hello hi!')

Output:
// {
//     "h": 2,
//     "e": 1,
//     "l": 2,
//     "o": 1,
//     "i": 1
// }
```

---
