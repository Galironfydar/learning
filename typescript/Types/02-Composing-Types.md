## Composing Types

with TypeScript, you can create complex types by combining simple ones.
There are two popular way to do so: with unions, and with generics.

### Unions

With a union, you can declare that a type could be one of many types. For example, you can describe a `boolean` type as bing either `true` or `false`:

```js
type MyBool = true | false;
    -> type MyBool = boolean
```

Note: if you hover over `MyBool` above, you'll see that is is classed as `boolean`. That's a property of the structural Type System. MOre on this below.

A popular use -case for union types is to decribe the set of `string` or `number` literals that a value is allowed to be: 

```js
type WindowStates = "open" | "closed" | "minimized";
type LockStates = "locked" | "unlocked";
type PositiveOddNumbersUnderTen = 1 | 3 | 5 | 7 | 9;
```

Unions prvide a way to handle different types too. For example, you may have a function that takes an `array` or a `string`:

```js
function getLength(obj: string | string[]) {
    return obj.length;
}
```