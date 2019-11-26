## ![logo](./lodash.svg)

[Lodash](https://lodash.com/docs/4.17.11)是一个著名的 javascript 原生库，不需要引入其他第三方依赖。是一个意在提高开发者效率,提高 JS 原生方法性能的 JS 库。

## ES6、ES7 盛行的今天，还有必要使用 Lodash 么？

网上一哥们整理一篇好文——[你并不需要 Underscore/Lodash](https://segmentfault.com/a/1190000004460234)，里面梳理了已经被原生支持的一些方法，大家可以参考参考

## Install

```
yarn add lodash
```

## USEGE

```js
 import { get } from 'lodash' ✘

 import get from 'lodash/get' √
```

## lodash 分类

- [Array](#array)
- [Collection](#collection) [“集合”是实现某种“迭代”接口的东西，它们在内部使用相同的迭代方法(尽管 Lodash 源比 Underscore 更复杂)。所有的“集合”都可以在数组和对象(以及更多的可迭代的事情)上起作用，而数组方法只能用于数组(或者也可以是.length 和数字索引的所有内容)]
- [Date](#date)
- [Function](#function)
- [Lang](#lang)
- [Math](#math)
- [Number](#number)
- [Object](#object)
- [Seq](#seq)
- [String](#string)
- [Util](#arUtilray)
- [Properties](#properties)

## Array

```js
_.chunk(["a", "b", "c", "d"], 2);
// => [['a', 'b'], ['c', 'd']]

_.chunk(["a", "b", "c", "d"], 3);
// => [['a', 'b', 'c'], ['d']]
```

```js
_.compact([0, 1, false, 2, "", 3]);
// => [1, 2, 3]
```

```js
var array = [1];
var other = _.concat(array, 2, [3], [[4]]);

console.log(other);
// => [1, 2, 3, [4]]

console.log(array);
// => [1]
```

```js
_.difference([2, 1], [2, 3]);
// => [1]
```

```js
_.intersection([2, 1], [2, 3]);
// => [2]
```

```js
_.drop([1, 2, 3]);
// => [2, 3]

_.drop([1, 2, 3], 2);
// => [3]

_.drop([1, 2, 3], 5);
// => []

_.drop([1, 2, 3], 0);
// => [1, 2, 3]
```

```js
var array = [1, 2, 3];

_.fill(array, "a");
console.log(array);
// => ['a', 'a', 'a']

_.fill(Array(3), 2);
// => [2, 2, 2]

_.fill([4, 6, 8, 10], "*", 1, 3);
// => [4, '*', '*', 10]
```

```js
var users = [
  { user: "barney", active: false },
  { user: "fred", active: false },
  { user: "pebbles", active: true }
];

_.findIndex(users, function(o) {
  return o.user == "barney";
});
// => 0

// The `_.matches` iteratee shorthand.
_.findIndex(users, { user: "fred", active: false });
// => 1

// The `_.matchesProperty` iteratee shorthand.
_.findIndex(users, ["active", false]);
// => 0

// The `_.property` iteratee shorthand.
_.findIndex(users, "active");
// => 2
```

```js
_.head([1, 2, 3]);
// => 1

_.head([]);
// => undefined
```

```js
_.tail([1, 2, 3]);
// => [2, 3]

_.tail(undefined);
// => []
```

```js
_.drop([1, 2, 3]);
// => [2, 3]
```

```js
_.last([1, 2, 3]);
// => 3
```

```js
_.initial([1, 2, 3]);
// => [1, 2]
```

```js
var array = ["a", "b", "c", "a", "b", "c"];

_.pull(array, "a", "c");
console.log(array);
// => ['b', 'b']
```

```js
_.union([1, 2, 3, 4], [2, 3, 4], [5, 6, 7]);
// => [1, 2, 3, 4, 5, 6, 7]
```

## Collection

```js
_.countBy([6.1, 4.2, 6.3], Math.floor);
// => { '4': 1, '6': 2 }
```

```js
_.forEach([1, 2], function(value) {
  console.log(value);
});
// => Logs `1` then `2`.
```

## Date

## Function

## Lang

## Math

## Number

## Object

## Seq

## String

## Util

## Properties

## 应用场景

```js
const flattenKeys = (obj, path = []) =>
  !_.isObject(obj)
    ? { [path.join(".")]: obj }
    : _.reduce(
        obj,
        (cum, next, key) => _.merge(cum, flattenKeys(next, [...path, key])),
        {}
      );

flattenKeys({ a: { e: 1, f: 2 }, b: 3, c: { g: 4 } });

// => {a.e: 1, a.f: 2, b: 3, c.g: 4}
```
