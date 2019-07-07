# Function as Value

As you progress in your Javascript career, you'll hear very often that `function` is a 
first-class citizen of the language. What does this mean?

Turns out in Javascript, `function`s are like regular values like `2` or `"hello"`. 
You can assign them to variables, pass them as parameters and also return them from functions.

You may ask: **Why not just call them as is? Why bother passing them around?**. It's a fair question.

The short answer: **That's how Javascript system works in your browser.**. We'll cover this in the next section.

In the mean time, let's go through a few exercises to pass/return `function`s in Javascript.

### Returning `function` object

**Let's write a function `incrBy(howMuch)` that returns a function (say `rFn`). 
`rFn(v)` takes one argument and returns `howMuch + v`**

```javascript
function incrBy(howMuch) {
  let rFn = function(v) {
    return howMuch + v;
  };
  return rFn;
}

let incrementBy5 = incrBy(5);
let incrementBy2 = incrBy(2);

console.log(incrementBy5(10)); // 15
```

**Advanced**: Can you think of a one-line version of `incrBy`?

### Passing `function` as parameter

Not only you can return `function`s in Javascript, you can also pass function as argument.

Let's start with the following code example

```javascript
function add2ToAll(arr) {
  let newArray = [];
  for (let i = 0; i < arr.length; i++) {
    newArray.push(arr[i] + 2);
  }
}

console.log(add2ToAll([1, 2, 3])); // [3, 4, 5]
```

We can extract the `arr[i] + 2` as a function.

```javascript
function add2ToAll(arr) {
  let newArray = [];
  let add2 = x => x + 2;
  for (let i = 0; i < arr.length; i++) {
    newArray.push(add2(arr[i]));
  }
}

console.log(add2ToAll([1, 2, 3])); // [3, 4, 5]
```

We can take this one step further and extract `add2` as an argument.

```javascript
function applyToAll(fn, arr) {
  let newArray = [];
  for (let i = 0; i < arr.length; i++) {
    newArray.push(fn(arr[i]));
  }
}

const add2 = x => x + 2;
console.log(applyToAll(add2, [1, 2, 3])); // [3, 4, 5]
```

In `applyToAll`, we moved `fn` up as an argument. And we moved define `add2` outside of `applyToAll` 
and pass it as an argument.

Sidenote: Later you'll learn that `applyToAll` is also called `map`

**Extra**: Can you use the `applyToAll` function to multiply all elements of an array by 10?

### (Optional) Another example

Let's try doing the same to `sumUp`. How do we start?

```javascript
function sumUp(arr) {
  let total = 0;
  for (let i = 0, i < arr.length, i++) {
    total = total + arr[i];
  }
  return total;
}
```

We can extract `total + arr[i]` as a function! Let's also rename `total` as `accumulated`.

```javascript
function sumUp(arr) {
  let accumulated = 0;
  let add = (a, b) => a + b;
  for (let i = 0, i < arr.length, i++) {
    accumulated = add(accumulated, arr[i]);
  }
  return accumulated;
}

console.log(sumUp([1, 2, 3, 4])); // 10
```

Now let's try to pull out `add` as a function argument! We will also pass `0` in as an argument.

```javascript
function fold(fn, initialValue, arr) {
  let accumulated = initialValue;
  for (let i = 0, i < arr.length, i++) {
    accumulated = fn(accumulated, arr[i]);
  }
  return accumulated;
}

let add = (a, b) => a + b;
console.log(fold(add, 0, [1, 2, 3, 4])); // 10
```

Sidenote: Later you'll learn that `fold` is also called `reduce`

We can go one step further! Rather than a function `fold` that takes 3 arguments, 
let's change `fold` so it becomes a function with 2 arguments, and it returns 
a function that takes an array as argument.

```javascript
function fold(fn, initialValue) {    // we only change this line and the following line
  return (arr) => {
    let accumulated = initialValue;
    for (let i = 0, i < arr.length, i++) {
      accumulated = fn(accumulated, arr[i]);
    }
    return accumulated;
  };
}

let add = (a, b) => a + b;
let sumUp = fold(add, 0);
console.log(sumUp([1, 2, 3, 4])); // 10
```

**Extra**: Why is `fold` useful? Let's explore it with some use cases.

```javascript
let add = (a, b) => a + b;
let mult = (a, b) => a * b;

let sumUp = fold(add, 0);
console.log(sumUp([1, 2, 3, 4])); // sum up an array 

let multiplyAll = fold(mult, 1);
console.log(multiplyAll([1, 2, 3, 4])); // multiply the whole an array

let bigger = (a, b) => {
  if (a > b) { return a; }
  return b;
};
let max = fold(bigger, 0);

console.log(max([1, 2, 3, 4])); // largest number in the array
```


