# Promise

Promise is a pretty recent addition to Javascript (ES2015 edition) to relieve the pain from **callbacks**

## Exercise

For the following exercises, we'll be using the Starwars API (https://swapi.co).

Let's start with this base code

```javascript
var rp = require('request-promise');

rp(`https://swapi.co/api/people/1`)
  .then(body => JSON.parse(body))
  .then(person => {
    console.log(person.name);
  });
```

This should print out `Luke Skywalker`.

### Exercise 1

Print out Luke's hair color. (Hint: `hair_color`)

Answer: `blond`

```javascript
var rp = require('request-promise');

rp(`https://swapi.co/api/people/1`)
  .then(body => JSON.parse(body))
  .then(person => {
    console.log(person.hair_color);
  });
```

### Exercise 2

What is Luke's home world? And what is the population?

Let's start with a plan!
1. get the URL from person.homeworld
2. use `rp` that load data from that URL
3. when the result is ready, print out world.name and world.population

Hint: try using string interpolation: ``console.log(`${world.name} ${world.population}`)``

Answer: 

```javascript
var rp = require('request-promise');

rp(`https://swapi.co/api/people/1`)
  .then(body => JSON.parse(body))
  .then(person => {
    // Plan:
    // 1) get the URL from person.homeworld
    // 2) `fetch` that URL
    // 3) when the result is ready, print out world.name and world.population

    let url = person.homeworld;
    rp(url)
      .then(body => JSON.parse(body))
      .then(world => {
        console.log(`${world.name} ${world.population}`);
      });
  });
```
