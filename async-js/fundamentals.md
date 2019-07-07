# Fundamentals

Before you are introduced to Async Javascript, let's warm up with a few exercises to review some core concepts of Javascript.

## Defining and Using functions

**Let's start with defining a function `add2(x, y)` that adds the 2 numbers and returns the result.**

Answer: 

```javascript
function add2(x, y) {
  return x + y;
}

console.log(add2(1, 2)); // 3
```

or

```javascript
const add2 = (x, y) => x + y;

console.log(add2(2, 3)); // 5
```

**Let's write another function `add4(a, b, c, d)` that adds up all the parameters and returns the result.**

Answer:

```javascript
function add4(a, b, c, d) {
  return a + b + c + d;
}

console.log(add4(1, 2, 3, 4)); // 10
```

Now, can you implement `add4` without using the `+` operator?

Answer: 


```javascript
function add4(a, b, c, d) {
  return add2(add2(a, b), add2(c, d));
}

console.log(add4(1, 2, 3, 4)); // 10
```

## Working with Arrays

**Let's write a function `printArray` that prints each of the elements of an array on it's own line.**

Hint: 

- `for` loop (first part is initialize, second part is **continuation condition**, last part is **increment step**)

```javascript
function printArray(arr) {
  for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
  }
}

printArray([1, 2, 3, 4]);
```

Extra: Try writing this with `for (let value of arr)` [(documentation)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of#Iterating_over_an_Array)

