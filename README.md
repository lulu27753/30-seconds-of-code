
## Table of Contents

### Array
* [Array difference](#array-difference)
* [Array intersection](#array-intersection)
* [Array pull (mutates array)](#array-pull-mutates-array)
* [Array remove](#array-remove)
* [Array sample](#array-sample)
* [Array symmetric difference](#array-symmetric-difference)
* [Array union](#array-union)
* [Array without](#array-without)
* [Array zip](#array-zip)
* [Average of array of numbers](#average-of-array-of-numbers)
* [Chunk array](#chunk-array)
* [Compact](#compact)
* [Count occurrences of a value in array](#count-occurrences-of-a-value-in-array)
* [Deep flatten array](#deep-flatten-array)
* [Drop elements in array](#drop-elements-in-array)
* [Filter out non unique values in an array](#filter-out-non-unique-values-in-an-array)
* [Flatten array up to depth](#flatten-array-up-to-depth)
* [Flatten array](#flatten-array)
* [Get max value from array](#get-max-value-from-array)
* [Get min value from array](#get-min-value-from-array)
* [Group by](#group-by)
* [Head of list](#head-of-list)
* [Initial of list](#initial-of-list)
* [Initialize array with range](#initialize-array-with-range)
* [Initialize array with values](#initialize-array-with-values)
* [Last of list](#last-of-list)
* [Median of array of numbers](#median-of-array-of-numbers)
* [Nth element of array](#nth-element-of-array)
* [Pick](#pick)
* [Shuffle array](#shuffle-array)
* [Similarity between arrays](#similarity-between-arrays)
* [Sum of array of numbers](#sum-of-array-of-numbers)
* [Tail of list](#tail-of-list)
* [Take every nth element](#take-every-nth-element)
* [Take right](#take-right)
* [Take](#take)
* [Unique values of array](#unique-values-of-array)

### Browser
* [Bottom visible](#bottom-visible)
* [Current URL](#current-url)
* [Element is visible in viewport](#element-is-visible-in-viewport)
* [Get scroll position](#get-scroll-position)
* [Redirect to URL](#redirect-to-url)
* [Scroll to top](#scroll-to-top)

### Date
* [Convert to english date](#convert-to-english-date)
* [Get days difference between dates](#get-days-difference-between-dates)
* [JSON to date](#json-to-date)

### Function
* [Chain asynchronous functions](#chain-asynchronous-functions)
* [Compose functions](#compose-functions)
* [Curry](#curry)
* [Log function name](#log-function-name)
* [Pipe functions](#pipe-functions)
* [Promisify](#promisify)
* [Run promises in series](#run-promises-in-series)
* [Sleep](#sleep)

### Math
* [Collatz algorithm](#collatz-algorithm)
* [Distance between two points](#distance-between-two-points)
* [Divisible by number](#divisible-by-number)
* [Even or odd number](#even-or-odd-number)
* [Factorial](#factorial)
* [Fibonacci array generator](#fibonacci-array-generator)
* [Greatest common divisor (GCD)](#greatest-common-divisor-gcd)
* [Hamming distance](#hamming-distance)
* [Least common multiple (LCM)](#least-common-multiple-lcm)
* [Percentile](#percentile)
* [Powerset](#powerset)
* [Random integer in range](#random-integer-in-range)
* [Random number in range](#random-number-in-range)
* [Round number to n digits](#round-number-to-n-digits)
* [Standard deviation](#standard-deviation)

### Media
* [Speech synthesis (experimental)](#speech-synthesis-experimental)

### Node
* [Read file as array of lines](#read-file-as-array-of-lines)
* [Write JSON to file](#write-json-to-file)

### Object
* [Clean JSON object](#clean-json-object)
* [Object from key value pairs](#object-from-key-value-pairs)
* [Object to key value pairs](#object-to-key-value-pairs)
* [Shallow clone object](#shallow-clone-object)

### String
* [Anagrams of string (with duplicates)](#anagrams-of-string-with-duplicates)
* [Capitalize first letter of every word](#capitalize-first-letter-of-every-word)
* [Capitalize first letter](#capitalize-first-letter)
* [Check for palindrome](#check-for-palindrome)
* [Convert string from camelcase](#convert-string-from-camelcase)
* [Convert string to camelcase](#convert-string-to-camelcase)
* [Reverse a string](#reverse-a-string)
* [Sort characters in string (alphabetical)](#sort-characters-in-string-alphabetical)
* [Truncate a string](#truncate-a-string)

### Utility
* [3 digit hexcode to 6 digit hexcode](#3-digit-hexcode-to-6-digit-hexcode)
* [Escape regular expression](#escape-regular-expression)
* [Get native type of value](#get-native-type-of-value)
* [Hexcode to RGB](#hexcode-to-rgb)
* [Is array](#is-array)
* [Is boolean](#is-boolean)
* [Is function](#is-function)
* [Is number](#is-number)
* [Is string](#is-string)
* [Is symbol](#is-symbol)
* [Measure time taken by function](#measure-time-taken-by-function)
* [Number to array of digits](#number-to-array-of-digits)
* [Ordinal suffix of number](#ordinal-suffix-of-number)
* [RGB to hexadecimal](#rgb-to-hexadecimal)
* [URL parameters](#url-parameters)
* [UUID generator](#uuid-generator)
* [Validate email](#validate-email)
* [Validate number](#validate-number)

## Array

### Array difference(数组之间的区别)

Create a `Set` from `b`, then use `Array.filter()` on `a` to only keep values not contained in `b`.
从b创建一个Set，然后在a上使用Array.filter（），只保留b中不包含的值。

```js
const difference = (a, b) => { const s = new Set(b); return a.filter(x => !s.has(x)); };
// difference([1,2,3], [1,2,4]) -> [3]
```

[⬆ back to top](#table-of-contents)

### Array intersection(两点之间的距离)

Create a `Set` from `b`, then use `Array.filter()` on `a` to only keep values contained in `b`.
使用Math.hypot（）计算两点之间的欧几里德距离。

```js
const intersection = (a, b) => { const s = new Set(b); return a.filter(x => s.has(x)); };
// intersection([1,2,3], [4,3,2]) -> [2,3]
```

[⬆ back to top](#table-of-contents)

### Array pull (mutates array)

Use `Array.filter()` and `Array.includes()` to pull out the values that are not needed. 
Use `Array.length = 0` to mutate the passed in array by resetting it's length to zero and `Array.push()` to re-populate it with only the pulled values.

```js
const pull = (arr, ...args) => {
  let pulled = arr.filter((v, i) => args.includes(v));
  arr.length = 0; pulled.forEach(v => arr.push(v));
};
// let myArray = ['a', 'b', 'c', 'a', 'b', 'c'];
// pull(myArray, 'a', 'c');
// console.log(myArray) -> [ 'b', 'b' ]
```

[⬆ back to top](#table-of-contents)

### Array remove

Use `Array.filter()` to find array elements that return truthy values and `Array.reduce()` to remove elements using `Array.splice()`.
The `func` is invoked with three arguments (`value, index, array`).

```js
const remove = (arr, func) =>
  Array.isArray(arr) ? arr.filter(func).reduce((acc, val) => {
    arr.splice(arr.indexOf(val), 1); return acc.concat(val);
    }, [])
  : [];
// remove([1, 2, 3, 4], n => n % 2 == 0) -> [2, 4]
```

[⬆ back to top](#table-of-contents)

### Array sample

Use `Math.random()` to generate a random number, multiply it with `length` and round it of to the nearest whole number using `Math.floor()`.
This method also works with strings.

```js
const sample = arr => arr[Math.floor(Math.random() * arr.length)];
// sample([3, 7, 9, 11]) -> 9
```

[⬆ back to top](#table-of-contents)

### Array symmetric difference

Create a `Set` from each array, then use `Array.filter()` on each of them to only keep values not contained in the other.

```js
const symmetricDifference = (a, b) => {
  const sA = new Set(a), sB = new Set(b);
  return [...a.filter(x => !sB.has(x)), ...b.filter(x => !sA.has(x))];
}
// symmetricDifference([1,2,3], [1,2,4]) -> [3,4]
```

[⬆ back to top](#table-of-contents)

### Array union

Create a `Set` with all values of `a` and `b` and convert to an array.

```js
const union = (a, b) => Array.from(new Set([...a, ...b]));
// union([1,2,3], [4,3,2]) -> [1,2,3,4]
```

[⬆ back to top](#table-of-contents)

### Array without

Use `Array.filter()` to create an array excluding(using `!Array.includes()`) all given values.

```js
const without = (arr, ...args) => arr.filter(v => !args.includes(v));
// without([2, 1, 2, 3], 1, 2) -> [3]
// without([2, 1, 2, 3, 4, 5, 5, 5, 3, 2, 7, 7], 3, 1, 5, 2) -> [ 4, 7, 7 ]
```

[⬆ back to top](#table-of-contents)

### Array zip

Use `Math.max.apply()` to get the longest array in the arguments.
Creates an array with that length as return value and use `Array.from()` with a map-function to create an array of grouped elements.
If lengths of the argument-arrays vary, `undefined` is used where no value could be found.

```js
const zip = (...arrays) => {
  const maxLength = Math.max(...arrays.map(x => x.length));
  return Array.from({length: maxLength}).map((_, i) => {
   return Array.from({length: arrays.length}, (_, k) => arrays[k][i]);
  })
}
//zip(['a', 'b'], [1, 2], [true, false]); -> [['a', 1, true], ['b', 2, false]]
//zip(['a'], [1, 2], [true, false]); -> [['a', 1, true], [undefined, 2, false]]
```

[⬆ back to top](#table-of-contents)

### Average of array of numbers(数组平均数)

Use `Array.reduce()` to add each value to an accumulator, initialized with a value of `0`, divide by the `length` of the array.
使用reduce（）将每个值添加到累加器，初始值为0，总和除以数组长度。
```js
const average = arr => arr.reduce((acc, val) => acc + val, 0) / arr.length;
// average([1,2,3]) -> 2
```

[⬆ back to top](#table-of-contents)

### Chunk array

Use `Array.from()` to create a new array, that fits the number of chunks that will be produced.
Use `Array.slice()` to map each element of the new array to a chunk the length of `size`.
If the original array can't be split evenly, the final chunk will contain the remaining elements.

```js
const chunk = (arr, size) =>
  Array.from({length: Math.ceil(arr.length / size)}, (v, i) => arr.slice(i * size, i * size + size));
// chunk([1,2,3,4,5], 2) -> [[1,2],[3,4],[5]]
```

[⬆ back to top](#table-of-contents)

### Compact

Use `Array.filter()` to filter out falsey values (`false`, `null`, `0`, `""`, `undefined`, and `NaN`).

```js
const compact = (arr) => arr.filter(Boolean);
// compact([0, 1, false, 2, '', 3, 'a', 'e'*23, NaN, 's', 34]) -> [ 1, 2, 3, 'a', 's', 34 ]
```

[⬆ back to top](#table-of-contents)

### Count occurrences of a value in array(计数数组中值的出现次数)

Use `Array.reduce()` to increment a counter each time you encounter the specific value inside the array.
每次遇到数组中的特定值时，使用reduce（）来递增计数器。

```js
const countOccurrences = (arr, value) => arr.reduce((a, v) => v === value ? a + 1 : a + 0, 0);
// countOccurrences([1,1,2,1,2,3], 1) -> 3
```

[⬆ back to top](#table-of-contents)

### Deep flatten array

Use recursion.
Use `Array.concat()` with an empty array (`[]`) and the spread operator (`...`) to flatten an array.
Recursively flatten each element that is an array.
使用递归，使用reduce（）来获取所有不是数组的元素，flatten每个元素都是数组。

```js
const deepFlatten = arr => [].concat(...arr.map(v => Array.isArray(v) ? deepFlatten(v) : v));
// deepFlatten([1,[2],[[3],4],5]) -> [1,2,3,4,5]
```

[⬆ back to top](#table-of-contents)

### Drop elements in array

Loop through the array, using `Array.shift()` to drop the first element of the array until the returned value from the function is `true`. 
Returns the remaining elements.

```js
const dropElements = (arr, func) => {
  while (arr.length > 0 && !func(arr[0])) arr.shift();
  return arr;
};
// dropElements([1, 2, 3, 4], n => n >= 3) -> [3,4]
```

[⬆ back to top](#table-of-contents)

### Filter out non-unique values in an array(过滤数组中的非唯一值)

Use `Array.filter()` for an array containing only the unique values.
将Array.filter（）用于仅包含唯一值的数组。


```js
const filterNonUnique = arr => arr.filter(i => arr.indexOf(i) === arr.lastIndexOf(i));
// filterNonUnique([1,2,2,3,4,4,5]) -> [1,3,5]
```

[⬆ back to top](#table-of-contents)

### Flatten array up to depth

Use recursion, decrementing `depth` by 1 for each level of depth.
Use `Array.reduce()` and `Array.concat()` to merge elements or arrays.
Base case, for `depth` equal to `1` stops recursion.
Omit the second element, `depth` to flatten only to a depth of `1` (single flatten).

```js
const flattenDepth = (arr, depth = 1) =>
  depth != 1 ? arr.reduce((a, v) => a.concat(Array.isArray(v) ? flattenDepth(v, depth - 1) : v), [])
  : arr.reduce((a, v) => a.concat(v), []);
// flattenDepth([1,[2],[[[3],4],5]], 2) -> [1,2,[3],4,5]
```

[⬆ back to top](#table-of-contents)

### Flatten array(Flatten数组)

Use `Array.reduce()` to get all elements inside the array and `concat()` to flatten them.
使用reduce（）来获取数组中的所有元素，并使用concat（）来使它们flatten。

```js
const flatten = arr => arr.reduce((a, v) => a.concat(v), []);
// flatten([1,[2],3,4]) -> [1,2,3,4]
```

[⬆ back to top](#table-of-contents)

### Get max value from array(从数组中获取最大值)

Use `Math.max()` combined with the spread operator (`...`) to get the maximum value in the array.
使用Math.max（）与spread运算符（...）结合得到数组中的最大值。

```js
const arrayMax = arr => Math.max(...arr);
// arrayMax([10, 1, 5]) -> 10
```

[⬆ back to top](#table-of-contents)

### Get min value from array(从数组中获取最小值)

Use `Math.min()` combined with the spread operator (`...`) to get the minimum value in the array.
使用Math.min（）与spread运算符（...）结合得到数组中的最小值。

```js
const arrayMin = arr => Math.min(...arr);
// arrayMin([10, 1, 5]) -> 1
```

[⬆ back to top](#table-of-contents)

### Group by

Use `Array.map()` to map the values of an array to a function or property name.
Use `Array.reduce()` to create an object, where the keys are produced from the mapped results.

```js
const groupBy = (arr, func) =>
  arr.map(typeof func === 'function' ? func : val => val[func])
    .reduce((acc, val, i) => { acc[val] = (acc[val] || []).concat(arr[i]); return acc; }, {});
// groupBy([6.1, 4.2, 6.3], Math.floor) -> {4: [4.2], 6: [6.1, 6.3]}
// groupBy(['one', 'two', 'three'], 'length') -> {3: ['one', 'two'], 5: ['three']}
```

[⬆ back to top](#table-of-contents)

### Head of list

Use `arr[0]` to return the first element of the passed array.
返回ARR[0]

```js
const head = arr => arr[0];
// head([1,2,3]) -> 1
```

[⬆ back to top](#table-of-contents)

### Initial of list(list初始化)

Use `arr.slice(0,-1)`to return all but the last element of the array.
返回arr.slice（0，-1）

```js
const initial = arr => arr.slice(0, -1);
// initial([1,2,3]) -> [1,2]
```

[⬆ back to top](#table-of-contents)

### Initialize array with range(用range初始化数组)

Use `Array(end-start)` to create an array of the desired length, `Array.map()` to fill with the desired values in a range.
You can omit `start` to use a default value of `0`.
使用Array（end-start）创建所需长度的数组，使用map（）来填充范围中的所需值，可以省略start使用默认值0。

```js
const initializeArrayRange = (end, start = 0) =>
  Array.from({ length: end - start }).map((v, i) => i + start);
// initializeArrayRange(5) -> [0,1,2,3,4]
```

[⬆ back to top](#table-of-contents)

### Initialize array with values(用值初始化数组)

Use `Array(n)` to create an array of the desired length, `fill(v)` to fill it with the desired values.
You can omit `value` to use a default value of `0`.
使用Array（n）创建所需长度的数组，fill(v)以填充所需的值，可以忽略value使用默认值0。

```js
const initializeArray = (n, value = 0) => Array(n).fill(value);
// initializeArray(5, 2) -> [2,2,2,2,2]
```

[⬆ back to top](#table-of-contents)

### Last of list(列表的最后)

Use `arr.length - 1` to compute index of the last element of the given array and returning it.
返回arr.slice（-1）[0]

```js
const last = arr => arr[arr.length - 1];
// last([1,2,3]) -> 3
```

[⬆ back to top](#table-of-contents)

### Median of array of numbers

Find the middle of the array, use `Array.sort()` to sort the values.
Return the number at the midpoint if `length` is odd, otherwise the average of the two middle numbers.

```js
const median = arr => {
  const mid = Math.floor(arr.length / 2), nums = arr.sort((a, b) => a - b);
  return arr.length % 2 !== 0 ? nums[mid] : (nums[mid - 1] + nums[mid]) / 2;
};
// median([5,6,50,1,-5]) -> 5
// median([0,10,-2,7]) -> 3.5
```

[⬆ back to top](#table-of-contents)

### Nth element of array

Use `Array.slice()` to get an array containing the nth element at the first place. 
If the index is out of bounds, return `[]`.
Omit the second argument, `n`, to get the first element of the array.

```js
const nth = (arr, n=0) => (n>0? arr.slice(n,n+1) : arr.slice(n))[0];
// nth(['a','b','c'],1) -> 'b'
// nth(['a','b','b']-2) -> 'a'
```

[⬆ back to top](#table-of-contents)

### Pick

Use `Array.reduce()` to convert the filtered/picked keys back to a object with the corresponding key:value pair if the key exist in the obj.

```js
const pick = (obj, arr) =>
  arr.reduce((acc, curr) => (curr in obj && (acc[curr] = obj[curr]), acc), {});
// pick({ 'a': 1, 'b': '2', 'c': 3 }, ['a', 'c']) -> { 'a': 1, 'c': 3 }
// pick(object, ['a', 'c'])['a'] -> 1
```

[⬆ back to top](#table-of-contents)

### Shuffle array(随机化数组的顺序)

Use `Array.sort()` to reorder elements, using `Math.random()` in the comparator.
使用sort（）重新排序元素，利用Math.random（）来随机排序。

```js
const shuffle = arr => arr.sort(() => Math.random() - 0.5);
// shuffle([1,2,3]) -> [2,3,1]
```

[⬆ back to top](#table-of-contents)

### Similarity between arrays(数组之间的相似性)

Use `filter()` to remove values that are not part of `values`, determined using `includes()`.
使用filter（）移除不是values的一部分值，使用includes（）确定。

```js
const similarity = (arr, values) => arr.filter(v => values.includes(v));
// similarity([1,2,3], [1,2,4]) -> [1,2]
```

[⬆ back to top](#table-of-contents)

### Sum of array of numbers(数组总和)

Use `Array.reduce()` to add each value to an accumulator, initialized with a value of `0`.
使用reduce（）将每个值添加到累加器，初始化值为0。

```js
const sum = arr => arr.reduce((acc, val) => acc + val, 0);
// sum([1,2,3,4]) -> 10
```

[⬆ back to top](#table-of-contents)

### Tail of list(列表的tail)

Return `arr.slice(1)` if the array's `length` is more than `1`, otherwise return the whole array.
返回arr.slice（1）

```js
const tail = arr => arr.length > 1 ? arr.slice(1) : arr;
// tail([1,2,3]) -> [2,3]
// tail([1]) -> [1]
```

[⬆ back to top](#table-of-contents)

### Take every nth element

Use `Array.filter()` to create a new array that contains every nth element of a given array.

```js
const everynth = (arr, nth) => arr.filter((e, i) => i % nth === 0);
// everynth([1,2,3,4,5,6], 2) -> [ 1, 3, 5 ]
```

[⬆ back to top](#table-of-contents)

### Take right

Use `Array.slice()` to create a slice of the array with `n` elements taken from the end.

```js
const takeRight = (arr, n = 1) => arr.slice(arr.length - n, arr.length);
// takeRight([1, 2, 3], 2) -> [ 2, 3 ]
// takeRight([1, 2, 3]) -> [3]
```

[⬆ back to top](#table-of-contents)

### Take

Use `Array.slice()` to create a slice of the array with `n` elements taken from the beginning.

```js
const take = (arr, n = 1) => arr.slice(0, n);
// take([1, 2, 3], 5) -> [1, 2, 3]
// take([1, 2, 3], 0) -> []
```

[⬆ back to top](#table-of-contents)

### Unique values of array(数组唯一值)

Use ES6 `Set` and the `...rest` operator to discard all duplicated values.
使用ES6 Set和... rest操作符去掉所有重复值。

```js
const unique = arr => [...new Set(arr)];
// unique([1,2,2,3,4,4,5]) -> [1,2,3,4,5]
```

[⬆ back to top](#table-of-contents)
## Browser

### Bottom visible

Use `scrollY`, `scrollHeight` and `clientHeight` to determine if the bottom of the page is visible.

```js
const bottomVisible = () =>
  document.documentElement.clientHeight + window.scrollY >= document.documentElement.scrollHeight || document.documentElement.clientHeight;
// bottomVisible() -> true
```

[⬆ back to top](#table-of-contents)

### Current URL(当前URL)

Use `window.location.href` to get current URL.
使用window.location.href来获取当前URL。

```js
const currentUrl = () => window.location.href;
// currentUrl() -> 'https://google.com'
```

[⬆ back to top](#table-of-contents)

### Element is visible in viewport

Use `Element.getBoundingClientRect()` and the `window.inner(Width|Height)` values
to determine if a given element is visible in the viewport.
Omit the second argument to determine if the element is entirely visible, or specify `true` to determine if
it is partially visible.

```js
const elementIsVisibleInViewport = (el, partiallyVisible = false) => {
  const { top, left, bottom, right } = el.getBoundingClientRect();
  return partiallyVisible
    ? ((top > 0 && top < innerHeight) || (bottom > 0 && bottom < innerHeight)) &&
      ((left > 0 && left < innerWidth) || (right > 0 && right < innerWidth))
    : top >= 0 && left >= 0 && bottom <= innerHeight && right <= innerWidth;
};
// e.g. 100x100 viewport and a 10x10px element at position {top: -1, left: 0, bottom: 9, right: 10}
// elementIsVisibleInViewport(el) -> false (not fully visible)
// elementIsVisibleInViewport(el, true) -> true (partially visible)
```

[⬆ back to top](#table-of-contents)

### Get scroll position(获取滚动位置)

Use `pageXOffset` and `pageYOffset` if they are defined, otherwise `scrollLeft` and `scrollTop`.
You can omit `el` to use a default value of `window`.
如果已定义，请使用pageXOffset和pageYOffset，否则使用scrollLeft和scrollTop，可以省略el来使用window的默认值。

```js
const getScrollPos = (el = window) =>
  ({x: (el.pageXOffset !== undefined) ? el.pageXOffset : el.scrollLeft,
    y: (el.pageYOffset !== undefined) ? el.pageYOffset : el.scrollTop});
// getScrollPos() -> {x: 0, y: 200}
```

[⬆ back to top](#table-of-contents)

### Redirect to URL(重定向到URL)

Use `window.location.href` or `window.location.replace()` to redirect to `url`.
Pass a second argument to simulate a link click (`true` - default) or an HTTP redirect (`false`).
使用window.location.href或window.location.replace（）重定向到url。 传递第二个参数来模拟链接点击（true - default）或HTTP重定向（false）。

```js
const redirect = (url, asLink = true) =>
  asLink ? window.location.href = url : window.location.replace(url);
// redirect('https://google.com')
```

[⬆ back to top](#table-of-contents)

### Scroll to top(滚动到顶部)

Get distance from top using `document.documentElement.scrollTop` or `document.body.scrollTop`.
Scroll by a fraction of the distance from top. Use `window.requestAnimationFrame()` to animate the scrolling.
使用document.documentElement.scrollTop或document.body.scrollTop获取到顶部的距离。
从顶部滚动一小部分距离。

使用window.requestAnimationFrame（）来滚动。

```js
const scrollToTop = () => {
  const c = document.documentElement.scrollTop || document.body.scrollTop;
  if (c > 0) {
    window.requestAnimationFrame(scrollToTop);
    window.scrollTo(0, c - c / 8);
  }
};
// scrollToTop()
```

[⬆ back to top](#table-of-contents)
## Date

### Convert to English date

Use `Date.toISOString()`, `split('T')` and `replace()` to convert a date from American format to English format.
Throws an error if the passed time cannot be converted to a date.

```js
const toEnglishDate  = (time) =>
  {try{return new Date(time).toISOString().split('T')[0].replace(/-/g, '/')}catch(e){return}};
// toEnglishDate('09/21/2010') -> '21/09/2010'
```

[⬆ back to top](#table-of-contents)

### Get days difference between dates

Calculate the difference (in days) between to `Date` objects.

```js
const getDaysDiffBetweenDates = (dateInitial, dateFinal) => (dateFinal - dateInitial) / (1000 * 3600 * 24);
// getDaysDiffBetweenDates(new Date("2017-12-13"), new Date("2017-12-22")) -> 9
```

[⬆ back to top](#table-of-contents)

### JSON to date

Use `Date()`, to convert dates in JSON format to readable format (`dd/mm/yyyy`).

```js
const jsonToDate = arr => {
  const dt = new Date(parseInt(arr.toString().substr(6)));
  return `${ dt.getDate() }/${ dt.getMonth() + 1 }/${ dt.getFullYear() }`
};
// jsonToDate(/Date(1489525200000)/) -> "14/3/2017"
```

[⬆ back to top](#table-of-contents)
## Function

### Chain asynchronous functions

Loop through an array of functions containing asynchronous events, calling `next` when each asynchronous event has completed.

```js
const chainAsync = fns => { let curr = 0; const next = () => fns[curr++](next); next(); };
/*
chainAsync([
  next => { console.log('0 seconds'); setTimeout(next, 1000); },
  next => { console.log('1 second');  setTimeout(next, 1000); },
  next => { console.log('2 seconds'); }
])
*/
```

[⬆ back to top](#table-of-contents)

### Compose functions

Use `Array.reduce()` to perform right-to-left function composition.
The last (rightmost) function can accept one or more arguments; the remaining functions must be unary.

```js
const compose = (...fns) => fns.reduce((f, g) => (...args) => f(g(...args)));
/*
const add5 = x => x + 5
const multiply = (x, y) => x * y
const multiplyAndAdd5 = compose(add5, multiply)
multiplyAndAdd5(5, 2) -> 15
*/
```

[⬆ back to top](#table-of-contents)

### Curry

Use recursion.
If the number of provided arguments (`args`) is sufficient, call the passed function `f`.
Otherwise return a curried function `f` that expects the rest of the arguments.
If you want to curry a function that accepts a variable number of arguments (a variadic function, e.g. `Math.min()`), you can optionally pass the number of arguments to the second parameter `arity`.
使用递归。如果提供的参数（args）数量足够，则调用传递函数f，否则返回一个curried函数f。

```js
const curry = (fn, arity = fn.length, ...args) =>
  arity <= args.length
    ? fn(...args)
    : curry.bind(null, fn, arity, ...args);
// curry(Math.pow)(2)(10) -> 1024
// curry(Math.min, 3)(10)(50)(2) -> 2
```

[⬆ back to top](#table-of-contents)

### Log function name

Use `console.debug()` and the `name` property of the passed method to log the method's name to the `debug` channel of the console.

```js
const functionName = fn => (console.debug(fn.name), fn);
// functionName(Math.max) -> max (logged in debug channel of console)
```

[⬆ back to top](#table-of-contents)

### Pipe functions(管道)

Use `Array.reduce()` with the spread operator (`...`) to perform left-to-right function composition.
The first (leftmost) function can accept one or more arguments; the remaining functions must be unary.
使用Array.reduce（）通过函数传递值。

```js
const pipe = (...fns) => fns.reduce((f, g) => (...args) => g(f(...args)));
/*
const add5 = x => x + 5
const multiply = (x, y) => x * y
const multiplyAndAdd5 = pipe(multiply, add5)
multiplyAndAdd5(5, 2) -> 15
*/
```

[⬆ back to top](#table-of-contents)

### Promisify

Use currying to return a function returning a `Promise` that calls the original function. 
Use the `...rest` operator to pass in all the parameters. 

*In Node 8+, you can use [`util.promisify`](https://nodejs.org/api/util.html#util_util_promisify_original)*

```js
const promisify = func =>
  (...args) =>
    new Promise((resolve, reject) =>
      func(...args, (err, result) =>
        err ? reject(err) : resolve(result))
    );
// const delay = promisify((d, cb) => setTimeout(cb, d))
// delay(2000).then(() => console.log('Hi!')) -> Promise resolves after 2s
```

[⬆ back to top](#table-of-contents)

### Run promises in series

Run an array of promises in series using `Array.reduce()` by creating a promise chain, where each promise returns the next promise when resolved.

```js
const series = ps => ps.reduce((p, next) => p.then(next), Promise.resolve());
// const delay = (d) => new Promise(r => setTimeout(r, d))
// series([() => delay(1000), () => delay(2000)]) -> executes each promise sequentially, taking a total of 3 seconds to complete
```

[⬆ back to top](#table-of-contents)

### Sleep

Delay executing part of an `async` function, by putting it to sleep, returning a `Promise`.

```js
const sleep = ms => new Promise(resolve => setTimeout(resolve, ms));
/*
async function sleepyWork() {
  console.log('I\'m going to sleep for 1 second.');
  await sleep(1000);
  console.log('I woke up after 1 second.');
}
*/
```

[⬆ back to top](#table-of-contents)
## Math

### Collatz algorithm

If `n` is even, return `n/2`. Otherwise  return `3n+1`.

```js
const collatz = n => (n % 2 == 0) ? (n / 2) : (3 * n + 1);
// collatz(8) --> 4
// collatz(5) --> 16
```

[⬆ back to top](#table-of-contents)

### Distance between two points

Use `Math.hypot()` to calculate the Euclidean distance between two points.

```js
const distance = (x0, y0, x1, y1) => Math.hypot(x1 - x0, y1 - y0);
// distance(1,1, 2,3) -> 2.23606797749979
```

[⬆ back to top](#table-of-contents)

### Divisible by number(可以按数字整除)

Use the modulo operator (`%`) to check if the remainder is equal to `0`.
使用模运算符（％）来检查余数是否等于0。

```js
const isDivisible = (dividend, divisor) => dividend % divisor === 0;
// isDivisible(6,3) -> true
```

[⬆ back to top](#table-of-contents)

### Even or odd number(偶数或奇数)

Checks whether a number is odd or even using the modulo (`%`) operator.
Returns `true` if the number is even, `false` if the number is odd.
使用Math.abs（）将逻辑扩展为负数，使用模（％）运算符进行检查。 如果数字是偶数，则返回true；如果数字是奇数，则返回false。

```js
const isEven = num => num % 2 === 0;
// isEven(3) -> false
```

[⬆ back to top](#table-of-contents)

### Factorial(阶乘)

Use recursion.
If `n` is less than or equal to `1`, return `1`.
Otherwise, return the product of `n` and the factorial of `n - 1`.
Throws an exception if `n` is a negative number.
使用递归。如果n小于或等于1，则返回1。否则返回n和n - 1的阶乘的乘积。

```js
const factorial = n =>
  n < 0 ? (() => { throw new TypeError('Negative numbers are not allowed!') })()
  : n <= 1 ? 1 : n * factorial(n - 1);
// factorial(6) -> 720
```

[⬆ back to top](#table-of-contents)

### Fibonacci array generator(斐波那契数组生成器)

Create an empty array of the specific length, initializing the first two values (`0` and `1`).
Use `Array.reduce()` to add values into the array, using the sum of the last two values, except for the first two.
创建一个特定长度的空数组，初始化前两个值（0和1）。使用Array.reduce（）向数组中添加值，后面的一个数等于前面两个数相加之和（前两个除外）。

```js
const fibonacci = n =>
  Array(n).fill(0).reduce((acc, val, i) => acc.concat(i > 1 ? acc[i - 1] + acc[i - 2] : i), []);
// fibonacci(5) -> [0,1,1,2,3]
```

[⬆ back to top](#table-of-contents)

### Greatest common divisor (GCD)(最大公约数)

Use recursion.
Base case is when `y` equals `0`. In this case, return `x`.
Otherwise, return the GCD of `y` and the remainder of the division `x/y`.
使用递归。基本情况是当y等于0时。在这种情况下，返回x。否则，返回y的GCD和x / y的其余部分。

```js
const gcd = (x, y) => !y ? x : gcd(y, x % y);
// gcd (8, 36) -> 4
```

[⬆ back to top](#table-of-contents)

### Hamming distance

Use XOR operator (`^`) to find the bit difference between the two numbers, convert to binary string using `toString(2)`.
Count and return the number of `1`s in the string, using `match(/1/g)`.

```js
const hammingDistance = (num1, num2) =>
  ((num1 ^ num2).toString(2).match(/1/g) || '').length;
// hammingDistance(2,3) -> 1
```

[⬆ back to top](#table-of-contents)

### Least common multiple (LCM)

Use the greatest common divisor (GCD) formula and `Math.abs()` to determine the least common multiple.
The GCD formula uses recursion.

```js
const lcm = (x,y) => {
  const gcd = (x, y) => !y ? x : gcd(y, x % y);
  return Math.abs(x*y)/(gcd(x,y));
};
// lcm(12,7) -> 84
```

[⬆ back to top](#table-of-contents)

### Percentile

Use `Array.reduce()` to calculate how many numbers are below the value and how many are the same value and
apply the percentile formula.

```js
const percentile = (arr, val) => 
  100 * arr.reduce((acc,v) => acc + (v < val ? 1 : 0) + (v === val ? 0.5 : 0), 0) / arr.length;
// percentile([1,2,3,4,5,6,7,8,9,10], 6) -> 55
 ```

[⬆ back to top](#table-of-contents)

### Powerset

Use `Array.reduce()` combined with `Array.map()` to iterate over elements and combine into an array containing all combinations.
使用reduce（）与map（）结合来遍历元素，并将其组合成包含所有组合的数组。

```js
const powerset = arr =>
  arr.reduce((a, v) => a.concat(a.map(r => [v].concat(r))), [[]]);
// powerset([1,2]) -> [[], [1], [2], [2,1]]
```

[⬆ back to top](#table-of-contents)

### Random integer in range(范围内的随机整数)

Use `Math.random()` to generate a random number and map it to the desired range, using `Math.floor()` to make it an integer.
使用Math.random（）生成一个随机数并将其映射到所需的范围，使用Math.floor（）使其成为一个整数。

```js
const randomIntegerInRange = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;
// randomIntegerInRange(0, 5) -> 2
```

[⬆ back to top](#table-of-contents)

### Random number in range(范围内的随机数)

Use `Math.random()` to generate a random value, map it to the desired range using multiplication.
使用Math.random（）生成一个随机值，使用乘法将其映射到所需的范围。

```js
const randomInRange = (min, max) => Math.random() * (max - min) + min;
// randomInRange(2,10) -> 6.0211363285087005
```

[⬆ back to top](#table-of-contents)

### Round number to n digits

Use `Math.round()` and template literals to round the number to the specified number of digits.
Omit the second argument, `decimals` to round to an integer.

```js
const round = (n, decimals=0) => Number(`${Math.round(`${n}e${decimals}`)}e-${decimals}`);
// round(1.005, 2) -> 1.01
```

[⬆ back to top](#table-of-contents)

### Standard deviation

Use `Array.reduce()` to calculate the mean, variance and the sum of the variance of the values, the variance of the values, then
determine the standard deviation.
You can omit the second argument to get the sample standard deviation or set it to `true` to get the population standard deviation.

```js
const standardDeviation = (arr, usePopulation = false) => {
  const mean = arr.reduce((acc, val) => acc + val, 0) / arr.length;
  return Math.sqrt(
    arr.reduce((acc, val) => acc.concat(Math.pow(val - mean, 2)), [])
       .reduce((acc, val) => acc + val, 0) / (arr.length - (usePopulation ? 0 : 1))
  );
};
// standardDeviation([10,2,38,23,38,23,21]) -> 13.284434142114991 (sample)
// standardDeviation([10,2,38,23,38,23,21], true) -> 12.29899614287479 (population)
```

[⬆ back to top](#table-of-contents)
## Media

### Speech synthesis (experimental)

Use `SpeechSynthesisUtterance.voice` and `window.speechSynthesis.getVoices()` to convert a message to speech.
Use `window.speechSynthesis.speak()` to play the message.

Learn more about the [SpeechSynthesisUtterance interface of the Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisUtterance).

```js
const speak = message => {
  const msg = new SpeechSynthesisUtterance(message);
  msg.voice = window.speechSynthesis.getVoices()[0];
  window.speechSynthesis.speak(msg);
};
// speak('Hello, World') -> plays the message
```

[⬆ back to top](#table-of-contents)
## Node

### Read file as array of lines

Use `readFileSync` function in `fs` node package to create a `Buffer` from a file.
convert buffer to string using `toString(encoding)` function.
creating an array from contents of file by `split`ing file content line by line(each `\n`).

  ```js
const fs = require('fs');
const readFileToArray = filename => fs.readFileSync(filename).toString('UTF8').split('\n');
/*
  contents of test.txt :
    line1
    line2
    line3
    ___________________________
  let arr = readFileToArray('test.txt')
  console.log(arr) // -> ['line1', 'line2', 'line3']
 */
```

[⬆ back to top](#table-of-contents)

### Write JSON to file

Use `fs.writeFile()`, template literals and `JSON.stringify()` to write a `json` object to a `.json` file.

```js
const fs = require('fs');
const jsonToFile = (obj, filename) => fs.writeFile(`${filename}.json`, JSON.stringify(obj, null, 2))
// jsonToFile({test: "is passed"}, 'testJsonFile') -> writes the object to 'testJsonFile.json'
```

[⬆ back to top](#table-of-contents)
## Object

### Clean JSON object

Use `Object.keys()` method to loop over given json object and deleting keys that are not `include`d in given array.
also if you give it a special key(`childIndicator`) it will search deeply inside it to apply function to inner objects too.

```js
const cleanObj = (obj, keysToKeep = [], childIndicator) => {
  Object.keys(obj).forEach(key => {
    if (key === childIndicator) {
      cleanObj(obj[key], keysToKeep, childIndicator);
    } else if (!keysToKeep.includes(key)) {
      delete obj[key];
    }
  })
}
/*
  testObj = {a: 1, b: 2, children: {a: 1, b: 2}}
  cleanObj(testObj, ["a"],"children")
  console.log(testObj)// { a: 1, children : { a: 1}}
*/
```

[⬆ back to top](#table-of-contents)

### Object from key-value pairs(来自键值对的对象)

Use `Array.reduce()` to create and combine key-value pairs.
使用Array.reduce（）来创建和组合键值对。

```js
const objectFromPairs = arr => arr.reduce((a, v) => (a[v[0]] = v[1], a), {});
// objectFromPairs([['a',1],['b',2]]) -> {a: 1, b: 2}
```

[⬆ back to top](#table-of-contents)

### Object to key-value pairs

Use `Object.keys()` and `Array.map()` to iterate over the object's keys and produce an array with key-value pairs.

```js
const objectToPairs = obj => Object.keys(obj).map(k => [k, obj[k]]);
// objectToPairs({a: 1, b: 2}) -> [['a',1],['b',2]])
```

[⬆ back to top](#table-of-contents)

### Shallow clone object

Use `Object.assign()` and an empty object (`{}`) to create a shallow clone of the original.

```js
const shallowClone = obj => Object.assign({}, obj);
/*
const a = { x: true, y: 1 };
const b = shallowClone(a);
a === b -> false
*/
```

[⬆ back to top](#table-of-contents)
## String

### Anagrams of string (with duplicates)

Use recursion.
For each letter in the given string, create all the partial anagrams for the rest of its letters.
Use `Array.map()` to combine the letter with each partial anagram, then `Array.reduce()` to combine all anagrams in one array.
Base cases are for string `length` equal to `2` or `1`.
使用递归。
对于给定字符串中的每个字母，为字母创建字谜。使用map（）将字母与每部分字谜组合，然后使用reduce（）将所有字谜组合到一个数组中，最基本情况是字符串长度等于2或1。

```js
const anagrams = str => {
  if (str.length <= 2) return str.length === 2 ? [str, str[1] + str[0]] : [str];
  return str.split('').reduce((acc, letter, i) =>
    acc.concat(anagrams(str.slice(0, i) + str.slice(i + 1)).map(val => letter + val)), []);
};
// anagrams('abc') -> ['abc','acb','bac','bca','cab','cba']
```

[⬆ back to top](#table-of-contents)

### Capitalize first letter of every word(大写每个单词的首字母)

Use `replace()` to match the first character of each word and `toUpperCase()` to capitalize it.
使用replace（）匹配每个单词的第一个字符，并使用toUpperCase（）来将其大写。

```js
const capitalizeEveryWord = str => str.replace(/\b[a-z]/g, char => char.toUpperCase());
// capitalizeEveryWord('hello world!') -> 'Hello World!'
```

[⬆ back to top](#table-of-contents)

### Capitalize first letter(首字母大写)

Use destructuring and `toUpperCase()` to capitalize first letter, `...rest` to get array of characters after first letter and then `Array.join('')` to make it a string again.
Omit the `lowerRest` parameter to keep the rest of the string intact, or set it to `true` to convert to lower case.
使用slice（0,1）和toUpperCase（）大写第一个字母，slice（1）获取字符串的其余部分。 省略lowerRest参数以保持字符串的其余部分不变，或将其设置为true以转换为小写。（注意：这和上一个示例不是同一件事情）

```js
const capitalize = ([first,...rest], lowerRest = false) =>
  first.toUpperCase() + (lowerRest ? rest.join('').toLowerCase() : rest.join(''));
// capitalize('myName') -> 'MyName'
// capitalize('myName', true) -> 'Myname'
```

[⬆ back to top](#table-of-contents)

### Check for palindrome(检查回文)

Convert string `toLowerCase()` and use `replace()` to remove non-alphanumeric characters from it.
Then, `split('')` into individual characters, `reverse()`, `join('')` and compare to the original, unreversed string, after converting it `tolowerCase()`.
将字符串转换为toLowerCase（），并使用replace（）从中删除非字母的字符。然后，将其转换为tolowerCase（），将（''）拆分为单独字符，reverse（），join（''），与原始的非反转字符串进行比较，然后将其转换为tolowerCase（）。

```js
const palindrome = str => {
  const s = str.toLowerCase().replace(/[\W_]/g,'');
  return s === s.split('').reverse().join('');
}
// palindrome('taco cat') -> true
 ```

[⬆ back to top](#table-of-contents)

### Convert string from camelcase

Use `replace()` to remove underscores, hyphens and spaces and convert words to camelcase.
Omit the scond argument to use a default separator of '_'.

```js
const fromCamelCase = (str, separator = '_') => 
  str.replace(/([a-z\d])([A-Z])/g, '$1' + separator + '$2')
    .replace(/([A-Z]+)([A-Z][a-z\d]+)/g, '$1' + separator + '$2').toLowerCase();
// fromCamelCase('someDatabaseFieldName', ' ') -> 'some database field name'
// fromCamelCase('someLabelThatNeedsToBeCamelized', '-') -> 'some-label-that-needs-to-be-camelized'
// fromCamelCase('someJavascriptProperty', '_') -> 'some_javascript_property'
```

[⬆ back to top](#table-of-contents)

### Convert string to camelcase

Use `replace()` to remove underscores, hyphens and spaces and convert words to camelcase.

```js
const toCamelCase = str => 
  str.replace(/^([A-Z])|[\s-_]+(\w)/g, (match, p1, p2, offset) =>  p2 ? p2.toUpperCase() : p1.toLowerCase());
// toCamelCase("some_database_field_name") -> 'someDatabaseFieldName'
// toCamelCase("Some label that needs to be camelized") -> 'someLabelThatNeedsToBeCamelized'
// toCamelCase("some-javascript-property") -> 'someJavascriptProperty'
// toCamelCase("some-mixed_string with spaces_underscores-and-hyphens") -> 'someMixedStringWithSpacesUnderscoresAndHyphens'
```

[⬆ back to top](#table-of-contents)

### Reverse a string(反转一个字符串)

Use array destructuring and `Array.reverse()` to reverse the order of the characters in the string.
Combine characters to get a string using `join('')`.
使用数组解构和Array.reverse（）来颠倒字符串中的字符顺序。合并字符以使用join('')获取字符串。

```js
const reverseString = str => [...str].reverse().join('');
// reverseString('foobar') -> 'raboof'
```

[⬆ back to top](#table-of-contents)

### Sort characters in string (alphabetical)(按字符串排序（按字母顺序排列）)

Split the string using `split('')`, `Array.sort()` utilizing `localeCompare()`, recombine using `join('')`.
使用split（''）分割字符串，sort（）使用localeCompare（），使用join（''）重新组合。

```js
const sortCharactersInString = str =>
  str.split('').sort((a, b) => a.localeCompare(b)).join('');
// sortCharactersInString('cabbage') -> 'aabbceg'
```

[⬆ back to top](#table-of-contents)

### Truncate a String

Determine if the string's `length` is greater than `num`.
Return the string truncated to the desired length, with `...` appended to the end or the original string.

```js
const truncate = (str, num) =>
  str.length > num ? str.slice(0, num > 3 ? num - 3 : num) + '...' : str;
// truncate('boomerang', 7) -> 'boom...'
```

[⬆ back to top](#table-of-contents)
## Utility

### 3-digit hexcode to 6-digit hexcode

Use `Array.map()`, `split()` and `Array.join()` to join the mapped array for converting a three-digit RGB notated hexadecimal color-code to the six-digit form.
`Array.slice()` is used to remove `#` from string start since it's added once.
```js
const convertHex = shortHex =>
  '#' + shortHex.slice(shortHex.startsWith('#') ? 1 : 0).split().map(x => x+x).join()
// convertHex('#03f') -> '#0033ff'
// convertHex('05a') -> '#0055aa'
```

[⬆ back to top](#table-of-contents)

### Escape regular expression(转义正则表达式)

Use `replace()` to escape special characters.
使用replace（）来转义特殊字符。

```js
const escapeRegExp = str => str.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
// escapeRegExp('(test)') -> \\(test\\)
```

[⬆ back to top](#table-of-contents)

### Get native type of value

Returns lower-cased constructor name of value, "undefined" or "null" if value is undefined or null

```js
const getType = v =>
  v === undefined ? 'undefined' : v === null ? 'null' : v.constructor.name.toLowerCase();
// getType(new Set([1,2,3])) -> "set"
```

[⬆ back to top](#table-of-contents)

### Hexcode to RGB

Use bitwise right-shift operator and mask bits with `&` (and) operator to convert a hexadecimal color code (prefixed with `#`) to a string with the RGB values.

```js
const hexToRgb = hex => {
  const h = parseInt(hex.slice(1), 16);
  return `rgb(${h >> 16}, ${(h & 0x00ff00) >> 8}, ${h & 0x0000ff})`;
}
// hexToRgb('#27ae60') -> 'rgb(39, 174, 96)'
```

[⬆ back to top](#table-of-contents)

### Is array

Use `Array.isArray()` to check if a value is classified as an array.

```js
const isArray = val => !!val && Array.isArray(val);
// isArray(null) -> false
// isArray([1]) -> true
```

[⬆ back to top](#table-of-contents)

### Is boolean

Use `typeof` to check if a value is classified as a boolean primitive.

```js
const isBoolean = val => typeof val === 'boolean';
// isBoolean(null) -> false
// isBoolean(false) -> true
```

[⬆ back to top](#table-of-contents)

### Is function

Use `typeof` to check if a value is classified as a function primitive.

```js
const isFunction = val => val && typeof val === 'function';
// isFunction('x') -> false
// isFunction(x => x) -> true
```

[⬆ back to top](#table-of-contents)

### Is number

Use `typeof` to check if a value is classified as a number primitive.

```js
const isNumber = val => typeof val === 'number';
// isNumber('1') -> false
// isNumber(1) -> true
```

[⬆ back to top](#table-of-contents)

### Is string

Use `typeof` to check if a value is classified as a string primitive.

```js
const isString = val => typeof val === 'string';
// isString(10) -> false
// isString('10') -> true
```

[⬆ back to top](#table-of-contents)

### Is symbol

Use `typeof` to check if a value is classified as a symbol primitive.

```js
const isSymbol = val => typeof val === 'symbol';
// isSymbol('x') -> false
// isSymbol(Symbol('x')) -> true
```

[⬆ back to top](#table-of-contents)

### Measure time taken by function(测试功能所花费的时间)

Use `console.time()` and `console.timeEnd()` to measure the difference between the start and end times to determine how long the callback took to execute.
使用performance.now（）获取函数的开始和结束时间，console.log（）所花费的时间。第一个参数是函数名，随后的参数传递给函数。

```js
const timeTaken = callback => {
  console.time('timeTaken');
  const r = callback();
  console.timeEnd('timeTaken');
  return r;
};
// timeTaken(() => Math.pow(2, 10)) -> 1024
// (logged): timeTaken: 0.02099609375ms
```

[⬆ back to top](#table-of-contents)

### Number to array of digits

Convert the number to a string, using spread operators in ES6(`[...string]`) build an array.
Use `Array.map()` and `parseInt()` to transform each value to an integer. 

```js
const digitize = n => [...''+n].map(i => parseInt(i));
// digitize(2334) -> [2, 3, 3, 4]
```

[⬆ back to top](#table-of-contents)

### Ordinal suffix of number

Use the modulo operator (`%`) to find values of single and tens digits.
Find which ordinal pattern digits match.
If digit is found in teens pattern, use teens ordinal.

```js
const toOrdinalSuffix = num => {
  const int = parseInt(num), digits = [(int % 10), (int % 100)],
    ordinals = ['st', 'nd', 'rd', 'th'], oPattern = [1, 2, 3, 4],
    tPattern = [11, 12, 13, 14, 15, 16, 17, 18, 19];
  return oPattern.includes(digits[0]) && !tPattern.includes(digits[1]) ? int + ordinals[digits[0] - 1] : int + ordinals[3];
};
// toOrdinalSuffix("123") -> "123rd"
```

[⬆ back to top](#table-of-contents)

### RGB to hexadecimal(RGB到十六进制)

Convert given RGB parameters to hexadecimal string using bitwise left-shift operator (`<<`) and `toString(16)`, then `padStart(6,'0')` to get a 6-digit hexadecimal value.
使用按位左移运算符（<<）和toString（16），然后padStart（6，“0”）将给定的RGB参数转换为十六进制字符串以获得6位十六进制值。

```js
const rgbToHex = (r, g, b) => ((r << 16) + (g << 8) + b).toString(16).padStart(6, '0');
// rgbToHex(255, 165, 1) -> 'ffa501'
```

[⬆ back to top](#table-of-contents)

### URL parameters(URL参数)

Use `match()` with an appropriate regular expression to get all key-value pairs, `Array.reduce()` to map and combine them into a single object.
Pass `location.search` as the argument to apply to the current `url`.
使用match() 与适当的正则表达式来获得所有键值对，适当的map() 。使用Object.assign（）和spread运算符（...）将所有键值对组合到一个对象中，将location.search作为参数传递给当前url。

```js
const getUrlParameters = url =>
  url.match(/([^?=&]+)(=([^&]*))/g).reduce(
    (a, v) => (a[v.slice(0, v.indexOf('='))] = v.slice(v.indexOf('=') + 1), a), {}
  );
// getUrlParameters('http://url.com/page?name=Adam&surname=Smith') -> {name: 'Adam', surname: 'Smith'}
```

[⬆ back to top](#table-of-contents)

### UUID generator(UUID生成器)

Use `crypto` API to generate a UUID, compliant with [RFC4122](https://www.ietf.org/rfc/rfc4122.txt) version 4.
使用crypto API生成符合RFC4122版本4的UUID。

```js
const uuid = () =>
  ([1e7] + -1e3 + -4e3 + -8e3 + -1e11).replace(/[018]/g, c =>
    (c ^ crypto.getRandomValues(new Uint8Array(1))[0] & 15 >> c / 4).toString(16)
  );
// uuid() -> '7982fcfe-5721-4632-bede-6000885be57d'
```

[⬆ back to top](#table-of-contents)

### Validate email

Use a regular expression to check if the email is valid.
Returns `true` if email is valid, `false` if not.

```js
const validateEmail = str =>
  /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/.test(str);
// validateEmail(mymail@gmail.com) -> true
```

[⬆ back to top](#table-of-contents)

### Validate number(验证数字)

Use `!isNaN` in combination with `parseFloat()` to check if the argument is a number.
Use `isFinite()` to check if the number is finite.
Use `Number()` to check if the coercion holds.
使用！isNaN和parseFloat（）来检查参数是否是一个数字，使用isFinite（）来检查数字是否是有限的。

```js
const validateNumber = n => !isNaN(parseFloat(n)) && isFinite(n) && Number(n) == n;
// validateNumber('10') -> true
```

[⬆ back to top](#table-of-contents)

## Credits

*Icons made by [Smashicons](https://www.flaticon.com/authors/smashicons) from [www.flaticon.com](https://www.flaticon.com/) is licensed by [CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/).*

