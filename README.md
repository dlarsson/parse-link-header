# parse-link-header [![build status](https://secure.travis-ci.org/thlorenz/parse-link-header.png)](http://travis-ci.org/thlorenz/parse-link-header)

[![testling badge](https://ci.testling.com/thlorenz/parse-link-header.png)](https://ci.testling.com/thlorenz/parse-link-header)

Parses a link header and returns paging information for each contained link.

```js
var parse = require('parse-link-header');

var linkHeader = 
  '<https://api.github.com/user/9287/repos?page=3&per_page=100>; rel="next", ' + 
  '<https://api.github.com/user/9287/repos?page=1&per_page=100>; rel="prev"; pet="cat", ' + 
  '<https://api.github.com/user/9287/repos?page=5&per_page=100>; rel="last"'

var parsed = parse(linkHeader);
console.log(parsed);
```

```js
{ next:
   { page: '3',
     per_page: '100',
     rel: 'next',
     url: 'https://api.github.com/user/9287/repos?page=3&per_page=100' },
  prev:
   { page: '1',
     per_page: '100',
     rel: 'prev',
     pet: 'cat',
     url: ' https://api.github.com/user/9287/repos?page=1&per_page=100' },
  last:
   { page: '5',
     per_page: '100',
     rel: 'last',
     url: ' https://api.github.com/user/9287/repos?page=5&per_page=100' } }
```

## Installation

    npm install parse-link-header

## API

***parseLinkHeader(linkHeader : String) : Object***

Parses the given link header containing [web links](http://tools.ietf.org/html/rfc5988) and returns an object keyed by
the `rel` property that contains information about each link.
