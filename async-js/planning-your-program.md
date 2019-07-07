# Planning Your Program

At this point, if I ask you how you would solve a problem with code, most of you would tell me there are 2 steps.

1. Read the problem
2. Write the code

Turns out even the most brilliant engineers cannot write code reliably with just these 2 steps. Here's my 5-step plan,

1. Read the problem
  - highlight keywords you find relevant (e.g. **each** generally means loop/iteration)
2. Write a plan to solve the problem
  - this plan is called **pseudocode**, it should focus on the main ideas that solves the problem but not real code
3. Does the plan solves the problem completely?
  - run some examples to make sure your plan works
4. Can you translate each step of the plan into a few lines of code? (for beginners: 1-3 lines)
  - if not, go back to Step 2
5. Translate each step into actual code


**Let's write another function `sumUp(arr)` that adds up an array of numbers and returns the result.**

But this time, we'll start with a plan and we start from the end. We know we'll need to return the `total` after summing up all numbers.
We also know that if we need to return `total`, we better initialize that variable

```
sumUp(arr) {
  total = 0
  ... 
  return total
}
```

To add up the whole array means we need a **loop**. Since we need to go through the whole array,

1. we need to start from 0
2. we need to increment by 1
3. we **continue** as long as the index is **less than** the array length

```
sumUp(arr) {
  total = 0 
  loop from i = 0, continue when i < arr.length, increment i by 1 {
    ...
  }
  return total
}
```

Now for each step, we need to add the element at index `i` to the total

```
sumUp(arr) {
  total = 0 
  loop from i = 0, continue when i < arr.length, increment i by 1 {
    total += arr[i]
  }
  return total
}
```

Now, let's check to see if this works for
- `[]` (empty array)
- `[1, 2, 3]`

Finally, we can convert the above plan into code. Notice that each line in the above plan converts to an exact line of code!

```javascript
function sumUp(arr) {
  let total = 0;
  for (let i = 0, i < arr.length, i++) {
    total += arr[i];
  }
  return total;
}

console.log(sumUp([]));  // 0
console.log(sumUp([1, 2, 3])); // 6
```
