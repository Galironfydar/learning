### Defining Types

- You can use a wide variety of design patterns in JavaScript. However, some design patterns make it difficult for type to be inferred automatically (for example, patterns that use dynamic programming). To cover these cases, TypeScript supports and extension of the JavaScript language, which offers places for you to tell TypeScript what the types should be.

For example, to create an oject with an inferred type which includes `name: string` and `id: number`, you can write:

```js
const user = {
    name: "John",
    id: 0,
}
```

You can explicitly descibe this object's shape using an `interface` declaration: 

```js
interface User {
    name: string,
    id: number,
}
```

You can then declare that a JavaScript object conforms to the shape of your new `interface` by using syntax like `: TypeName` after a variable declarations;

```js
const user: User = {
    name: "John",
    id: 0,
}
```

if you provide an object that doesn't match the interface you have procided, TypeScript will warn you:

```js
interface User {
    name: string,
    id: number,
}

const user: User = {
    username: "John",
    //Type '{ username: string; id: number; }' is not assignable to type 'User'.
    //Object literal may only specify known properties, and 'username' does not exist in type 'User'.
    id: 0,
}
```

Since JavaScript supports classes and object-oriented programming, so does TypeScript. You can use an interface declaration with classes:

```js
interface User {
    name: string;
    id: number;
}

class UserAccount {
    name: string;
    id: number;

    constructor(name: string, id: number) {
        this.name = name;
        this.id = id;
    }
}

const user: User = new UserAccount("Chris", 1);
```

You can use interfaces to annotate parameters and return values to functions: 

```js
function getAdminUser(): User {
    // return value
}

function deleteUser(user: User) {
    // parameter type hinting.
}
```

There is a lready a small set of primitive types available in JavaScript: `beelean`, `bigint`, `null`, `number`, `string`, `symbol`, and `undefined`, which you can use in an interface. TypeScript extends this list with a few more, such as `any` (allow anything), `unknown` (ensure someone using this type declares what the type is), `never` (it's not possible that this type could happen), and `void` (a function which returns `undefined` or has no return value)

You'll see that theres are two syntaxes for building types: [Interfaces and Types]. You should prefer `interface`. Use `type when you need specific features.


