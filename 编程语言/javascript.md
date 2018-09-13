## Array

### _.chunk

> Creates an array of elements split into groups the length of size.

```javascript
// Underscore/Lodash
_.chunk(['a', 'b', 'c', 'd'], 2);
// => [['a', 'b'], ['c', 'd']]

_.chunk(['a', 'b', 'c', 'd'], 3);
// => [['a', 'b', 'c'], ['d']]


// Native

const chunk = (input, size) => {
  return input.reduce((arr, item, idx) => {
    return idx % size === 0
      ? [...arr, [item]]
      : [...arr.slice(0, -1), [...arr.slice(-1)[0], item]];
  }, []);
};

chunk(['a', 'b', 'c', 'd'], 2);
// => [['a', 'b'], ['c', 'd']]

chunk(['a', 'b', 'c', 'd'], 3);
// => [['a', 'b', 'c'], ['d']]
```

### _.compact

> Creates an array with all falsy values removed.

```javascript
// Underscore/Lodash
_.compact([0, 1, false, 2, '', 3]);

// Native
[0, 1, false, 2, '', 3].filter(Boolean)
```

### _.concat

> Creates a new array concatenating array with any additional arrays and/or values.

```javascript
// Underscore/Lodash
var array = [1]
var other = _.concat(array, 2, [3], [[4]])

console.log(other)
// output: [1, 2, 3, [4]]

// Native
var array = [1]
var other = array.concat(2, [3], [[4]])

console.log(other)
// output: [1, 2, 3, [4]]
```

### _.fill

> Fills elements of array with value from start up to, but not including, end. Note that fill is a mutable method in both native and Lodash/Underscore.

```javascript
// Underscore/Lodash
var array = [1, 2, 3]

_.fill(array, 'a')

console.log(array)
// output: ['a', 'a', 'a']

_.fill(Array(3), 2)
// output: [2, 2, 2]

_.fill([4, 6, 8, 10], '*', 1, 3)
// output: [4, '*', '*', 10]

// Native
var array = [1, 2, 3]

array.fill('a')

console.log(array)
// output: ['a', 'a', 'a']

Array(3).fill(2)
// output: [2, 2, 2]

[4, 6, 8, 10].fill('*', 1, 3)
// output: [4, '*', '*', 10]
```

### _.find

> Returns the value of the first element in the array that satisfies the provided testing function. Otherwise undefined is returned.

```// Underscore/Lodash
var users = [
  { 'user': 'barney',  'age': 36, 'active': true },
  { 'user': 'fred',    'age': 40, 'active': false },
  { 'user': 'pebbles', 'age': 1,  'active': true }
]

_.find(users, function (o) { return o.age < 40; })
// output: object for 'barney'

// Native
var users = [
  { 'user': 'barney',  'age': 36, 'active': true },
  { 'user': 'fred',    'age': 40, 'active': false },
  { 'user': 'pebbles', 'age': 1,  'active': true }
]

users.find(function (o) { return o.age < 40; })
// output: object for 'barney'
```

### _.findIndex

> Returns the index of the first element in the array that satisfies the provided testing function. Otherwise -1 is returned.

```javascript
// Underscore/Lodash
var users = [
  { 'user': 'barney',  'age': 36, 'active': true },
  { 'user': 'fred',    'age': 40, 'active': false },
  { 'user': 'pebbles', 'age': 1,  'active': true }
]

var index = _.findIndex(users, function (o) { return o.age >= 40; })
console.log(index)
// output: 1

// Native
var users = [
  { 'user': 'barney',  'age': 36, 'active': true },
  { 'user': 'fred',    'age': 40, 'active': false },
  { 'user': 'pebbles', 'age': 1,  'active': true }
]

var index = users.findIndex(function (o) { return o.age >= 40; })
console.log(index)
// output: 1
```

### _.first

> Returns the first element of an array. Passing n will return the first n elements of the array.

```
// Underscore/Lodash
_.first([1, 2, 3, 4, 5]);
// => 1

_.first([1, 2, 3, 4, 5], 2);
// => [1, 2]

// Native
[1, 2, 3, 4, 5][0];
// => 1
//or
[].concat(1, 2, 3, 4, 5).shift()
// => 1
//or
[].concat([1, 2, 3, 4, 5]).shift()
// => 1

// Native (works even with potentially undefined/null, like _.first)
[].concat(undefined).shift()
// => undefined

[1, 2, 3, 4, 5].slice(0, 2);
// => [1, 2]
```

### _.flatten

> Flattens array a single level deep.

```javascript
// Underscore/Lodash
_.flatten([1, [2, [3, [4]], 5]]);
// => [1, 2, [3, [4]], 5]

// Native
const flatten = [1, [2, [3, [4]], 5]].reduce( (a, b) => a.concat(b), [])
// => [1, 2, [3, [4]], 5]
```

### _.flattenDeep

> Recursively flattens array.

```javascript
// Underscore/Lodash
_.flattenDeep([1, [2, [3, [4]], 5]]);
// => [1, 2, 3, 4, 5]

// Native
const flattenDeep = (arr) => Array.isArray(arr)
  ? arr.reduce( (a, b) => a.concat(flattenDeep(b)) , [])
  : [arr]

flattenDeep([1, [[2], [3, [4]], 5]])
// => [1, 2, 3, 4, 5]
```

### _.fromPairs

> Returns an object composed from key-value pairs.

```javascript
// Underscore/Lodash
_.fromPairs([['a', 1], ['b', 2]]);
// => { 'a': 1, 'b': 2 }

// Native
const fromPairs = function(arr) {
  return arr.reduce(function(accumulator, value) {
    accumulator[value[0]] = value[1];
    return accumulator;
  }, {})
}

// Compact form
const fromPairs = (arr) => arr.reduce((acc, val) => (acc[val[0]] = val[1], acc), {})

fromPairs([['a', 1], ['b', 2]]);
// => { 'a': 1, 'b': 2 }
```

### _.head and _.tail

> Gets the first element or all but the first element.

```javascript
const array = [1, 2, 3]

// Underscore: _.first, _.head, _.take
// Lodash: _.first, _.head
_.head(array)
// output: 1

// Underscore: _.rest, _.tail, _.drop
// Lodash: _.tail
_.tail(array)
// output: [2, 3]


// Native
const [ head, ...tail ] = array
console.log(head)
// output: 1
console.log(tail)
// output [2, 3]
```

### _.indexOf

> Returns the first index at which a given element can be found in the array, or -1 if it is not present.

```javascript
// Underscore/Lodash
var array = [2, 9, 9]
var result = _.indexOf(array, 2)
console.log(result)
// output: 0

// Native
var array = [2, 9, 9]
var result = array.indexOf(2)
console.log(result)
// output: 0
```

### _.join

> ❗️Lodash only Joins a list of elements in an array with a given separator.

```javascript
// Lodash
var result = _.join(['one', 'two', 'three'], '--')
console.log(result)
// output: 'one--two--three'

// Native
var result = ['one', 'two', 'three'].join('--')
console.log(result)
// output: 'one--two--three'
```

### _.last

> Returns the last element of an array. Passing n will return the last n elements of the array.

```javascript
// Underscore/Lodash
const numbers = [1, 2, 3, 4, 5];
_.last(numbers);
// => 5

_.last(numbers, 2);
// => [4, 5]

// Native
const numbers = [1, 2, 3, 4, 5];
numbers[numbers.length - 1];
// => 5
//or
numbers.slice(-1)[0];
// => 5
//or
[].concat(numbers).pop()
// => 5

// Native (works even with potentially undefined/null)
[].concat(undefined).pop()
// => undefined

numbers.slice(-2);
// => [4, 5]
```

### _.lastIndexOf

> Returns the index of the last occurrence of value in the array, or -1 if value is not present.

```javascript
// Underscore/Lodash
var array = [2, 9, 9, 4, 3, 6]
var result = _.lastIndexOf(array, 9)
console.log(result)
// output: 2

// Native
var array = [2, 9, 9, 4, 3, 6]
var result = array.lastIndexOf(9)
console.log(result)
// output: 2
```

### _.reverse

> ❗️Lodash only Reverses array so that the first element becomes the last, the second element becomes the second to last, and so on.

```javascript
// Lodash
var array = [1, 2, 3]
console.log(_.reverse(array))
// output: [3, 2, 1]

// Native
var array = [1, 2, 3]
console.log(array.reverse())
// output: [3, 2, 1]
```

### _.without

> ❗️Lodash only Returns an array where matching items are filtered.

```javascript
// Lodash
var array = [1, 2, 3]
console.log(_.without(array, 2))
// output: [1, 3]

// Native
var array = [1, 2, 3]
console.log(array.filter(function(value) {
  return value !== 2;
}));
// output: [1, 3]
```

### _.slice

> Returns a shallow copy of a portion of an array into a new array object selected from begin to end (end not included)

```javascript
// Lodash
var array = [1, 2, 3, 4]
console.log(_.slice(array, 1, 3))
// output: [2, 3]

// Native
var array = [1, 2, 3, 4]
console.log(array.slice(1, 3));
// output: [2, 3]
```

### _.isArray

> Returns true if given value is an array.

```javascript
// Lodash
var array = []
console.log(_.isArray(array))
// output: true

// Native
var array = []
console.log(Array.isArray(array));
// output: true
```

### _.isArrayBuffer

> Checks if value is classified as an ArrayBuffer object.

```javascript
// Lodash
_.isArrayBuffer(new ArrayBuffer(2));
// output: true

// Native
console.log(new ArrayBuffer(2) instanceof ArrayBuffer);
// output: true
```

## Collection

### _.each

> Iterates over a list of elements, yielding each in turn to an iteratee function.

```javascript
// Underscore/Lodash
_.each([1, 2, 3], function (value, index) {
  console.log(value)
})
// output: 1 2 3

// Native
[1, 2, 3].forEach(function (value, index) {
  console.log(value)
})
// output: 1 2 3
```

### _.every

> Tests whether all elements in the array pass the test implemented by the provided function.

```javascript
// Underscore/Lodash
function isLargerThanTen (element, index, array) {
  return element >= 10
}
var array = [10, 20, 30]
var result = _.every(array, isLargerThanTen)
console.log(result)
// output: true

// Native
function isLargerThanTen (element, index, array) {
  return element >= 10
}

var array = [10, 20, 30]
var result = array.every(isLargerThanTen)
console.log(result)
// output: true
```

### _.filter

> Creates a new array with all elements that pass the test implemented by the provided function.

```javascript
// Underscore/Lodash
function isBigEnough (value) {
  return value >= 10
}
var array = [12, 5, 8, 130, 44]
var filtered = _.filter(array, isBigEnough)
console.log(filtered)
// output: [12, 130, 44]

// Native
function isBigEnough (value) {
  return value >= 10
}
var array = [12, 5, 8, 130, 44]
var filtered = array.filter(isBigEnough)
console.log(filtered)
// output: [12, 130, 44]
```

### _.groupBy

```javascript
// Underscore/Lodash
var grouped = _.groupBy(['one', 'two', 'three'], 'length')
console.log(grouped)
// output: {3: ["one", "two"], 5: ["three"]}

// Native
var grouped = ['one', 'two', 'three'].reduce((r, v, i, a, k = v.length) => ((r[k] || (r[k] = [])).push(v), r), {})
console.log(grouped)
// output: {3: ["one", "two"], 5: ["three"]}
```

```javascript
// Underscore/Lodash
var grouped = _.groupBy([1.3, 2.1, 2.4], num => Math.floor(num))
console.log(grouped)
// output: {1: [1.3], 2: [2.1, 2.4]}

// Native
var grouped = [1.3, 2.1, 2.4].reduce((r, v, i, a, k = Math.floor(v)) => ((r[k] || (r[k] = [])).push(v), r), {})
console.log(grouped)
// output: {1: [1.3], 2: [2.1, 2.4]}
```

### _.includes

```javascript
var array = [1, 2, 3]
// Underscore/Lodash - also called _.contains
_.includes(array, 1)
// output: true

// Native
var array = [1, 2, 3]
array.includes(1)
// output: true

// Native (does not use same value zero)
var array = [1, 2, 3]
array.indexOf(1) > -1
// output: true
```

### _.map

> Translates all items in an array or object to new array of items.

```javascript
// Underscore/Lodash
var array1 = [1, 2, 3]
var array2 = _.map(array1, function (value, index) {
  return value * 2
})
console.log(array2)
// output: [2, 4, 6]

// Native
var array1 = [1, 2, 3]
var array2 = array1.map(function (value, index) {
  return value * 2
})
console.log(array2)
// output: [2, 4, 6]
```


### _.minBy and _.maxBy

> Use Array#reduce for find the maximum or minimum collection item

```javascript
// Underscore/Lodash
var data = [{ value: 6 }, { value: 2 }, { value: 4 }]
var minItem = _.minBy(data, 'value')
var maxItem = _.maxBy(data, 'value')
console.log(minItem, maxItem)
// output: { value: 2 } { value: 6 }

// Native
var data = [{ value: 6 }, { value: 2 }, { value: 4 }]
var minItem = data.reduce(function(a, b) { return a.value <= b.value ? a : b }, {})
var maxItem = data.reduce(function(a, b) { return a.value >= b.value ? a : b }, {})
console.log(minItem, maxItem)
// output: { value: 2 }, { value: 6 }
```

> Extract a functor and use es2015 for better code

```javascript
// utils
const makeSelect = (comparator) => (a, b) => comparator(a, b) ? a : b
const minByValue = makeSelect((a, b) => a.value <= b.value)
const maxByValue = makeSelect((a, b) => a.value >= b.value)

// main logic
const data = [{ value: 6 }, { value: 2 }, { value: 4 }]
const minItem = data.reduce(minByValue, {})
const maxItem = data.reduce(maxByValue, {})

console.log(minItem, maxItem)
// output: { value: 2 }, { value: 6 }

// or also more universal and little slower variant of minBy
const minBy = (collection, key) => {
  // slower because need to create a lambda function for each call...
  const select = (a, b) => a[key] <= b[key] ? a : b
  return collection.reduce(select, {})
}

console.log(minBy(data, 'value'))
// output: { value: 2 }
```

### _.pluck

> array.map or _.map can also be used to replace _.pluck. Lodash v4.0 removed _.pluck in favor of _.map with iteratee shorthand. Details can be found in Changelog

```javascript
// Underscore/Lodash
var array1 = [{name: "Alice"}, {name: "Bob"}, {name: "Jeremy"}]
var names = _.pluck(array1, "name")
console.log(names)
// output: ["Alice", "Bob", "Jeremy"]

// Native
var array1 = [{name: "Alice"}, {name: "Bob"}, {name: "Jeremy"}]
var names = array1.map(function(x){
  return x.name
})
console.log(names)
// output: ["Alice", "Bob", "Jeremy"]
```



### _.reduce

> Applies a function against an accumulator and each value of the array (from left-to-right) to reduce it to a single value.

```javascript
// Underscore/Lodash
var array = [0, 1, 2, 3, 4]
var result = _.reduce(array, function (previousValue, currentValue, currentIndex, array) {
  return previousValue + currentValue
})
console.log(result)
// output: 10

// Native
var array = [0, 1, 2, 3, 4]
var result = array.reduce(function (previousValue, currentValue, currentIndex, array) {
  return previousValue + currentValue
})
console.log(result)
// output: 10
```



### _.range

> Creates an array of numbers progressing from start up to.

```javascript
// Underscore/Lodash
_.range(4)  // output: [0, 1, 2, 3]
_.range(-4) // output: [0, -1, -2, -3]
_.range(1, 5)     // output: [1, 2, 3, 4]
_.range(0, 20, 5) // output: [0, 5, 10, 15]

// Native ( solution with Array.from )
Array.from({length: 4}, (_, i) => i)  // output: [0, 1, 2, 3]
Array.from({length: 4}, (_, i) => -i) // output: [0, -1, -2, -3]
Array.from({length: 4}, (_, i) => i + 1) // output: [1, 2, 3, 4]
Array.from({length: 4}, (_, i) => i * 5) // output: [0, 5, 10, 15]

// Native ( solution with keys() and spread )
[...Array(4).keys()] // output: [0, 1, 2, 3]
```


### _.reduceRight

> This method is like _.reduce except that it iterates over elements of collection from right to left.

```javascript
// Underscore/Lodash
var array = [0, 1, 2, 3, 4]
var result = _.reduceRight(array, function (previousValue, currentValue, currentIndex, array) {
  return previousValue - currentValue
})
console.log(result)
// output: -2

// Native
var array = [0, 1, 2, 3, 4]
var result = array.reduceRight(function (previousValue, currentValue, currentIndex, array) {
  return previousValue - currentValue
})
console.log(result)
// output: -2
```



### _.size

> Returns the number of values in the collection.

```javascript
// Underscore/Lodash
var result = _.size({one: 1, two: 2, three: 3})
console.log(result)
// output: 3

// Native
var result2 = Object.keys({one: 1, two: 2, three: 3}).length
console.log(result2)
// output: 3
```


### _.some

> Tests whether any of the elements in the array pass the test implemented by the provided function.

```javascript
// Underscore/Lodash
function isLargerThanTen (element, index, array) {
  return element >= 10
}
var array = [10, 9, 8]
var result = _.some(array, isLargerThanTen)
console.log(result)
// output: true

// Native
function isLargerThanTen (element, index, array) {
  return element >= 10
}

var array = [10, 9, 8]
var result = array.some(isLargerThanTen)
console.log(result)
// output: true
```


### _.sortBy and _.orderBy

> Sorts an array of object based on an object key provided by a parameter (note this is more limited than Underscore/Lodash).



```javascript
const fruits = [
  {name:"banana", amount: 2},
  {name:"apple", amount: 4},
  {name:"pineapple", amount: 2},
  {name:"mango", amount: 1}
];

// Underscore
_.sortBy(fruits, 'name');
// => [{name:"apple", amount: 4}, {name:"banana", amount: 2}, {name:"mango", amount: 1}, {name:"pineapple", amount: 2}]

// Lodash
_.orderBy(fruits, ['name'],['asc']);
// => [{name:"apple", amount: 4}, {name:"banana", amount: 2}, {name:"mango", amount: 1}, {name:"pineapple", amount: 2}]

// Native
const sortBy = (key) => {
  return (a, b) => (a[key] > b[key]) ? 1 : ((b[key] > a[key]) ? -1 : 0);
};

fruits.sort(sortBy("name"));
// => [{name:"apple", amount: 4}, {name:"banana", amount: 2}, {name:"mango", amount: 1}, {name:"pineapple", amount: 2}]
```


### _.uniq

> Produces a duplicate-free version of the array, using === to test object equality.

```javascript
// Underscore/Lodash
var array = [1, 2, 1, 4, 1, 3]
var result = _.uniq(array)
console.log(result)
// output: [1, 2, 4, 3]

// Native
var array = [1, 2, 1, 4, 1, 3];
var result = [...new Set(array)];
console.log(result)
// output: [1, 2, 4, 3]
```

## Function

### _.after

> ❗️Note this is an alternative implementation Creates a version of the function that will only be run after first being called count times. Useful for grouping asynchronous responses, where you want to be sure that all the async calls have finished, before proceeding.

```javascript
var notes = ['profile', 'settings']
// Underscore/Lodash
var renderNotes = _.after(notes.length, render)
notes.forEach(function (note) {
  console.log(note)
  renderNotes()
})

// Native
notes.forEach(function (note, index) {
  console.log(note)
  if (notes.length === (index + 1)) {
    render()
  }
})
```


### _.bind

> 

```javascript
```


###

> Create a new function that calls func with thisArg and args.

```javascript
var objA = {
  x: 66,
  offsetX: function(offset) {
    return this.x + offset;
  }
}

var objB = {
  x: 67
};

// Underscore/Lodash
var boundOffsetX = _.bind(objA.offsetX, objB, 0);

// Native
var boundOffsetX = objA.offsetX.bind(objB, 0);
```


### _.partial

> Create a new function that calls func with args.

```javascript
// Lodash
function greet(greeting, name) {
  return greeting + ' ' + name;
}
var sayHelloTo = _.partial(greet, 'hello');

// Native
function greet(greeting, name) {
  return greeting + ' ' + name;
}
var sayHelloTo = (...args) => greet('hello', ...args)
```

## Lang

### _.isNaN

> Checks if a value is NaN.

```javascript
// Underscore/Lodash
console.log(_.isNaN(NaN))
// output: true

// Native
console.log(isNaN(NaN))
// output: true

// ES6
console.log(Number.isNaN(NaN))
// output: true
```


### _.isUndefined

> Checks if value is undefined.

```javascript
// Underscore/Lodash
console.log(_.isUndefined(a))
// output: true

// Native
console.log(typeof a === 'undefined');
// output: true
console.log(a === undefined);
// output: true
```


### _.gt

> Checks if value is greater than other.

```javascript
// Lodash
console.log(_.gt(3, 1))
// output: true

// Native
console.log(3 > 1);
// output: true
```


### _.gte

> checks if value is greater than or equal to other.

```javascript
// Lodash
console.log(_.gte(3, 1))
// output: true

// Native
console.log(3 >= 1);
// output: true
```

## Objects


### _.assign

> The method is used to copy the values of all enumerable own properties from one or more source objects to a target object.

```javascript
// Underscore: _.extendOwn
// Lodash
function Foo() {
  this.c = 3;
}
function Bar() {
  this.e = 5;
}
Foo.prototype.d = 4;
Bar.prototype.f = 6;
var result = _.assign(new Foo, new Bar);
console.log(result);
// output: { 'c': 3, 'e': 5 }

// Native
function Foo() {
  this.c = 3;
}
function Bar() {
  this.e = 5;
}
Foo.prototype.d = 4;
Bar.prototype.f = 6;
var result = Object.assign({}, new Foo, new Bar);
console.log(result);
// output: { 'c': 3, 'e': 5 }
```



### _.keys

> Retrieves all the names of the object's own enumerable properties.

```javascript
// Underscore/Lodash
var result = _.keys({one: 1, two: 2, three: 3})
console.log(result)
// output: ["one", "two", "three"]

// Native
var result2 = Object.keys({one: 1, two: 2, three: 3})
console.log(result2)
// output: ["one", "two", "three"]
```



### _.toPairs

> Retrieves all the given object's own enumerable property [ key, value ] pairs.

```javascript
// Underscore - also called _.pairs
// Lodash - also called _.entries
var result = _.toPairs({one: 1, two: 2, three: 3})
console.log(result)
// output: [["one", 1], ["two", 2], ["three", 3]]

// Native
var result2 = Object.entries({one: 1, two: 2, three: 3})
console.log(result2)
// output: [["one", 1], ["two", 2], ["three", 3]]
```



### _.values

> Retrieves all the given object's own enumerable property values.

```javascript
// Underscore/Lodash
var result = _.values({one: 1, two: 2, three: 3})
console.log(result)
// output: [1, 2, 3]

// Native
var result2 = Object.values({one: 1, two: 2, three: 3})
console.log(result2)
// output: [1, 2, 3]
```



### _.get

> Gets the value at path of object. Note: If provided path does not exists inside the object js will generate error.

```javascript
// Lodash
var object = { a: [{ b: { c: 3 } }] };
var result = _.get(object, 'a[0].b.c', 1);
console.log(result);
// output: 3

// Native
var object = { a: [{ b: { c: 3 } }] };
var { a: [{ b: { c = 1 } }] } = object;
console.log(result);
// output: 3
```



### _.omit

> Returns a copy of the object, filtered to omit the keys specified.



```javascript
var object = { 'a': 1, 'b': '2', 'c': 3 };

// Underscore/Lodash
var result = _.omit(object, ['a', 'c']);
console.log(result)
// output: { 'b': '2' }

// Native
var { a, c, ...result2 } = object;
console.log(result2)
// output: { 'b': '2' }
```

## String


### _.repeat

> Lodash only Repeats the given string n times.

```javascript
// Lodash
var result = _.repeat('abc', 2)
// output: 'abcabc'

// Native
var result = 'abc'.repeat(2)
console.log(result)
// output: 'abcabc'
```



### _.template

> ❗️ Note this is an alternative implementation. Native template literals not escape html.

```javascript
// Lodash/Underscore
const compiled = _.template('hello <%= user %>!');
compiled({ 'user': 'fred' });

// Native
const templateLitreal = (value) => `hello ${value.user}`;
templateLitreal({ 'user': 'fred' });
```



### _.toLower

> ❗️Lodash only Lowercases a given string.

```javascript
// Lodash
var result = _.toLower('FOOBAR')
console.log(result)
// output: 'foobar'

// Native
var result = 'FOOBAR'.toLowerCase()
console.log(result)
// output: 'foobar'
```



### _.toUpper

> ❗️Lodash only Uppercases a given string.

```javascript
// Lodash
var result = _.toUpper('foobar')
console.log(result)
// output: 'FOOBAR'

// Native
var result = 'foobar'.toUpperCase()
console.log(result)
// output: 'FOOBAR'
```



### _.trim

> ❗️Lodash only Removes the leading and trailing whitespace characters from a string.

```javascript
// Lodash
var result = _.trim(' abc ')
console.log(result)
// output: 'abc'

// Native
var result = ' abc '.trim()
console.log(result)
// output: 'abc'
```



### _.replace

> returns a new string with some or all matches of a pattern replaced by a replacement

```javascript
// Lodash
var re = /apples/gi;
var str = 'Apples are round, and apples are juicy.';
var newstr = _.replace(str, re, 'oranges');
console.log(newstr);
// output: 'oranges are round, and oranges are juicy.'

// Native
var re = /apples/gi;
var str = 'Apples are round, and apples are juicy.';
var result = str.replace(re, 'oranges');
console.log(result);
// output: 'oranges are round, and oranges are juicy.'
```



### _.uniq

> Removes all duplicates entries from an array.

```javascript
// Underscore/Lodash
var result = _.uniq([1, 2, 1, 4, 1, 3]);
console.log(result)
// output: [1, 2, 4, 3]

// Native
var result = [... new Set([1, 2, 1, 4, 1, 3])]
console.log(result)
// output: [1, 2, 4, 3]
```

