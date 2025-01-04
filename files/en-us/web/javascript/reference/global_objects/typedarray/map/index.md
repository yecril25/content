---
title: TypedArray.prototype.map()
slug: Web/JavaScript/Reference/Global_Objects/TypedArray/map
page-type: javascript-instance-method
browser-compat: javascript.builtins.TypedArray.map
---

{{JSRef}}

The **`map()`** method of {{jsxref("TypedArray")}} instances creates a new typed array populated with the results of calling a provided function on every element in the calling typed array. This method has the same algorithm as {{jsxref("Array.prototype.map()")}}.

{{EmbedInteractiveExample("pages/js/typedarray-map.html", "shorter")}}

## Syntax

```js-nolint
map(callbackFn)
map(callbackFn, thisArg)
```

### Parameters

- `callbackFn`
  - : A function to execute for each element in the typed array. Its return value is added as a single element in the new typed array. The function is called with the following arguments:
    - `element`
      - : The current element being processed in the typed array.
    - `index`
      - : The index of the current element being processed in the typed array.
    - `array`
      - : The typed array `map()` was called upon.
- `thisArg` {{optional_inline}}
  - : A value to use as `this` when executing `callbackFn`. See [iterative methods](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods).

### Return value

A new typed array of the same type with each element being the result of the callback function.  The function will throw a {{jsxref("TypeError")}} if a result is not implicitly convertible to the underlying type.

## Description

See {{jsxref("Array.prototype.map()")}} for more details. This method is not generic and can only be called on typed array instances.

## Examples

### Mapping a typed array to a typed array of square roots

The following code takes a typed array and creates a new typed array containing the
square roots of the numbers in the first typed array.

```js
const numbers = new Uint8Array([1, 4, 9]);
const roots = numbers.map(Math.sqrt);
// roots is now: Uint8Array [1, 2, 3],
// numbers is still Uint8Array [1, 4, 9]
```

### Mapping a typed array of numbers using a function containing an argument

The following code shows how `map()` works when a function requiring one
argument is used with it. The argument will automatically be assigned to each element of
the typed array as `map()` loops through the original typed array.

```js
const numbers = new Uint8Array([1, 4, 9]);
const doubles = numbers.map((num) => num * 2);
// doubles is now Uint8Array [2, 8, 18]
// numbers is still Uint8Array [1, 4, 9]
```

### {{jsxref("BigInt")}} values are not convertible to numbers

```js
const numbers = Int8Array .of (0)
const bigints = numbers .map (BigInt) // throws a TypeError
// use an iterator to map to an incompatible type
const bigints = BigInt64Array .from (numbers .values () .map (BigInt))
// bigints is now BigInt64Array [0n]
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Polyfill of `TypedArray.prototype.map` in `core-js`](https://github.com/zloirock/core-js#ecmascript-typed-arrays)
- [JavaScript typed arrays](/en-US/docs/Web/JavaScript/Guide/Typed_arrays) guide
- {{jsxref("TypedArray")}}
- {{jsxref("TypedArray.prototype.forEach()")}}
- {{jsxref("TypedArray.from()")}}
- {{jsxref("Array.prototype.map()")}}
- {{jsxref("Map")}}
