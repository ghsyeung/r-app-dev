# Async and Await

Both `async` and `await` are new keywords in the new ES2017 specification. It has a more straight
forward syntax, which works as a complement to the **Promise** API.

Note that these keywords has no support in **IE** so you'll need `babel` and likely polyfill library
to make it work in **IE**.

## Exercise

For the following exercises, we'll be again using the Starwars API (https://swapi.co).

These exercises are the same as the ones in the [Promise](async-js/promise.md) section, so you can 
compare the **Promise** syntax and the **Async/Await** syntax directly.

Let's start with this base code

```javascript
var rp = require('request-promise');

async function run() {
  let body = await rp(`https://swapi.co/api/people/1`);
  let person = JSON.parse(body);

  console.log(person.name);
}

run();
```

This should print out `Luke Skywalker`.

### Exercise 1

Print out Luke's hair color. (Hint: `hair_color`)

Answer: `blond`

```javascript
var rp = require('request-promise');

async function run() {
  let body = await rp(`https://swapi.co/api/people/1`);
  let person = JSON.parse(body);

  console.log(person.hair_color);
}

run();
```

### Exercise 2

What is Luke's home world? And what is the population?

Answer: 

```javascript
var rp = require('request-promise');

async function run() {
  const body = await rp(`https://swapi.co/api/people/1`);
  const luke = JSON.parse(body);
  const homeworldUrl = luke.homeworld;

  const homeWorldBody = await rp(homeworldUrl);
  const world = JSON.parse(homeWorldBody);
  console.log(`${luke.name}'s home world is: ${world.name} ${world.population}`);
}

run();
```
