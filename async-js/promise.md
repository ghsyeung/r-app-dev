# Promise

Promise is a pretty recent addition to Javascript (ES2015 edition) to relieve the pain from **callbacks**

## Exercise

For the following exercises, we'll be using the Starwars API (https://swapi.co).

Let's start with this base code

{% runkit %}
require('request');
var rp = require('request-promise');

rp(`https://swapi.co/api/people/1`)
  .then(body => JSON.parse(body))
  .then(person => {
    console.log(person.name);
  });
{% endrunkit %}
