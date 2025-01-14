# Typescript

Created: August 20, 2023 11:48 AM
Updated: February 18, 2024 9:06 PM

Initial build

```
I need:
(1) git ignore
(2) pagkage json
(3) typescript and @types/node for dev
(4) tsconfing.json. posso startar esse arquivo usando tsc --init
(5) module-alias and @types/module-alias, this last one for dev
(6) -D ts-node-dev

```

```
posso compilar usando tsc e o nome do arquivo. preciso tb usar node(se a dependencia typescript tiver normal, se tiver como dev, que é o certo, tenho que usar o comando npx). mas tambem posso instalar o typescript global, e ai posso compilar sem precisar do comando node

```

Detecting errors in code without running it is referred to as ***static checking***. Determining what’s an error and what’s not based on the kinds of values being operated on is known as static ***type* checking**.

Roughly speaking, once TypeScript’s compiler is done with checking your code, it *erases* the types to produce the resulting “compiled” code. This means that once your code is compiled, the resulting plain JS code has no type information.

```
//anotar o parametro
function deleteUser(user: User) {
  // ...
}
//valor de retorno de uma função
function getAdminUser(): User {
  //...
}

```

There is already a small set of primitive types available in JavaScript: `boolean`, `bigint`, `null`, `number`, `string`, `symbol`, and `undefined`, which you can use in an interface. TypeScript extends this list with a few more, such as `any` (allow anything), `unknown` (ensure someone using this type declares what the type is), `never` (it’s not possible that this type could happen), and `void` (a function which returns `undefined` or has no return value).

## Composing Types

### Unions

With a union, you can declare that a type could be one of many types. For example, you can describe a booleantype as being either trueor false:

```
type MyBool = true | false;

```

A popular use-case for union types is to describe the set of `string` or `number` [literals](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#literal-types) that a value is allowed to be:

```
type WindowStates = "open" | "closed" | "minimized";
type LockStates = "locked" | "unlocked";
type PositiveOddNumbersUnderTen = 1 | 3 | 5 | 7 | 9;

```

For example, you can make a function return different values depending on whether it is passed a string or an array:

```
function wrapInArray(obj: string | string[]) {
  if (typeof obj === "string") {
    return [obj];

(parameter) obj: string
  }
  return obj;
}

```

### Generics

Generics provide variables to types. A common example is an array. An array without generics could contain anything. An array with generics can describe the values that the array contains.

```
type StringArray = Array<string>;
type NumberArray = Array<number>;
type ObjectWithNameArray = Array<{ name: string }>;

```

TypeScript has corresponding primitive types for the built-in types:

- number
- string
- bigint
- boolean
- symbol
- null
- undefined
- object

### Other important TypeScript types

| Type | Explanation |
| --- | --- |
| unknown | the top type. |
| never | the bottom type. |
| object literal | eg { property: Type } |
| void | for functions with no documented return value |
| T[] | mutable arrays, also written Array<T> |
| [T, T] | tuples, which are fixed-length but mutable |
| (t: T) => U | functions |

Object Literal: This refers to a type that describes the structure of an object using key-value pairs. An example is { property: Type }. Here, you define the property names as keys and their respective types as values. Object literals help to define the shape of an object, which is especially useful in TypeScript's type system for checking and enforcing structure.

## Explicit Types

```
function greet(person: string, date: Date) {
  console.log(`Hello ${person}, today is ${date.toDateString()}!`);
}

```

//  What we did was add *type annotations* on personand date

//You can read that signature as ”`greet` takes a `person` of type `string`, and a `date` of type `Date`“

# Everyday Types

number[ ]  === Array<number>

### Optional Properties

Object types can also specify that some or all of their properties are *optional*. To do this, add a ?after the property name:

```
function printName(obj: { first: string; last?: string }) {
  // ...
}
// Both OK
printName({ first: "Bob" });
printName({ first: "Alice", last: "Alisson" });

```

## Type Aliases

We’ve been using object types and union types by writing them directly in type annotations. This is convenient, but it’s common to want to use the same type more than once and refer to it by a single name.

A *type alias* is exactly that - a *name* for any *type*. The syntax for a type alias is:

```
type Point = {
  x: number;
  y: number;
};

// Exactly the same as the earlier example
function printCoord(pt: Point) {
  console.log("The coordinate's x value is " + pt.x);
  console.log("The coordinate's y value is " + pt.y);
}

printCoord({ x: 100, y: 100 });

```

You can actually use a type alias to give a name to any type at all, not just an object type. For example, a type alias can name a union type:

```
type ID = number | string;

```

You’ll see that there are two syntaxes for building types: [Interfaces and Types](https://www.typescriptlang.org/play/?e=83#example/types-vs-interfaces). You should prefer `interface`. Use `type` when you need specific features

### Differences Between Type Aliases and Interfaces

Type aliases and interfaces are very similar, and in many cases you can choose between them freely. Almost all features of an interfaceare available in type, the key distinction is that a type cannot be re-opened to add new properties vs an interface which is always extendable.

![Typescript%20c7d3d45df94e42c0afce9fd802d79f4e/image.png](Typescript%20c7d3d45df94e42c0afce9fd802d79f4e/image.png)

![Typescript%20c7d3d45df94e42c0afce9fd802d79f4e/image%201.png](Typescript%20c7d3d45df94e42c0afce9fd802d79f4e/image%201.png)

## Type Assertions

Sometimes you will have information about the type of a value that TypeScript can’t know about.

For example, if you’re using document.getElementById, TypeScript only knows that this will return *some*kind of HTMLElement, but you might know that your page will always have an HTMLCanvasElementwith a given ID.

In this situation, you can use a *type assertion*to specify a more specific type:

```
const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;

```

You can also use the angle-bracket syntax (except if the code is in a `.tsx` file), which is equivalent:

```
const myCanvas = <HTMLCanvasElement>document.getElementById("main_canvas");

```

Reminder: Because type assertions are removed at compile-time, there is no runtime checking associated with a type assertion. There won’t be an exception or `null` generated if the type assertion is wrong.

### Non-null Assertion Operator (Postfix !)

TypeScript also has a special syntax for removing nulland undefinedfrom a type without doing any explicit checking. Writing !after any expression is effectively a type assertion that the value isn’t nullor undefined:

```
function liveDangerously(x?: number | null) {
  // No error
  console.log(x!.toFixed());

```

## Enums

Enums are a feature added to JavaScript by TypeScript which allows for describing a value which could be one of a set of possible named constants. Unlike most TypeScript features, this is *not*a type-level addition to JavaScript but something added to the language and runtime. Because of this, it’s a feature which you should know exists, but maybe hold off on using unless you are sure. You can read more about enums in the [Enum reference page](https://www.typescriptlang.org/docs/handbook/enums.html).

## Narrowing

In TypeScript, narrowing refers to the process of refining the type of a variable within a certain code block based on certain conditions or type guards. This allows the TypeScript compiler to understand the more specific type of a variable within a certain scope, which can be useful for performing type-specific operations or avoiding type errors.

TypeScript achieves narrowing through type guards, which are expressions that perform runtime checks that guarantee the type of a variable. Some common constructs that act as type guards include typeof type guards, instanceof type guards, and user-defined type guards.

## Function Type Expressions

The simplest way to describe a function is with a *function type expression*. These types are syntactically similar to arrow functions:

```
function greeter(fn: (a: string) => void) {
  fn("Hello, World");
}

function printToConsole(s: string) {
  console.log(s);
}

greeter(printToConsole);

```

## Call Signatures

In JavaScript, functions can have properties in addition to being callable. However, the function type expression syntax doesn’t allow for declaring properties. If we want to describe something callable with properties, we can write a *call signature*in an object type:

```
type DescribableFunction = {
  description: string;
  (someArg: number): boolean;
};
function doSomething(fn: DescribableFunction) {
  console.log(fn.description + " returned " + fn(6));
}

function myFunc(someArg: number) {
  return someArg > 3;
}
myFunc.description = "default description";

doSomething(myFunc);
Try

```

Note that the syntax is slightly different compared to a function type expression - use :between the parameter list and the return type rather than =>

## Generic Functions

It’s common to write a function where the types of the input relate to the type of the output, or where the types of two inputs are related in some way. Let’s consider for a moment a function that returns the first element of an array:

```
function firstElement(arr: any[]) {
  return arr[0];
}
Try

```

This function does its job, but unfortunately has the return type any. It’d be better if the function returned the type of the array element.

In TypeScript, *generics*are used when we want to describe a correspondence between two values. We do this by declaring a *type parameter*in the function signature:

```
function firstElement<Type>(arr: Type[]): Type | undefined {
  return arr[0];
}

```

## Optional Parameters

Functions in JavaScript often take a variable number of arguments. For example, the toFixedmethod of numbertakes an optional digit count:

We can model this in TypeScript by marking the parameter as *optional* with `?`:

```
function f(x?: number) {
  // ...
}
f(); // OK
f(10); // OK

```

# Object types

### Index Signatures

Sometimes you don’t know all the names of a type’s properties ahead of time, but you do know the shape of the values.

In those cases you can use an index signature to describe the types of possible values, for example:

```
interface StringArray {
  [index: number]: string;
}

const myArray: StringArray = getStringArray();
const secondItem = myArray[1];
          const secondItem: string
Try

```

Above, we have a StringArrayinterface which has an index signature. This index signature states that when a StringArrayis indexed with a number, it will return a string.

## Extending Types

The `extends` keyword on an `interface` allows us to effectively copy members from other named types, and add whatever new members we want. This can be useful for cutting down the amount of type declaration boilerplate we have to write, and for signaling intent that several different declarations of the same property might be related.

```
interface BasicAddress {
  name?: string;
  street: string;
  city: string;
  country: string;
  postalCode: string;
}

interface AddressWithUnit extends BasicAddress {
  unit: string;
}
Try

```

# Generics

Instead, we can make a *generic* Boxtype which declares a *type parameter*.

```tsx
interface Box<Type> {
  contents: Type;
}

```

You might read this as “A Boxof Typeis something whose contentshave type Type”. Later on, when we refer to Box, we have to give a *type argument*in place of Type.

```tsx
let box: Box<string>;

```

`Box` is reusable in that `Type` can be substituted with anything. That means that when we need a box for a new type, we don’t need to declare a new `Box` type at all (though we certainly could if we wanted to).

```tsx
interface Box<Type> {
  contents: Type;
}

interface Apple {
  // ....
}

// Same as '{ contents: Apple }'.
type AppleBox = Box<Apple>;

```

### The Array Type

Generic object types are often some sort of container type that work independently of the type of elements they contain. It’s ideal for data structures to work this way so that they’re re-usable across different data types.

It turns out we’ve been working with a type just like that throughout this handbook: the Arraytype. Whenever we write out types like number[]or string[], that’s really just a shorthand for Array<number>and Array<string>.

```tsx
function doSomething(value: Array<string>) {
  // ...
}

let myArray: string[] = ["hello", "world"];

// either of these work!
doSomething(myArray);
doSomething(new Array("hello", "world"));
Try

```

Much like the Boxtype above, Arrayitself is a generic type.

```tsx
interface Array<Type> {
  /**
   * Gets or sets the length of the array.
   */
  length: number;

  /**
   * Removes the last element from an array and returns it.
   */
  pop(): Type | undefined;

  /**
   * Appends new elements to an array, and returns the new length of the array.
   */
  push(...items: Type[]): number;

  // ...
}
Try

```

Modern JavaScript also provides other data structures which are generic, like Map<K, V>, Set<T>, and Promise<T>. All this really means is that because of how Map, Set, and Promisebehave, they can work with any sets of types.

In previous sections, we created generic identity functions that worked over a range of types. In this section, we’ll explore the type of the functions themselves and how to create generic interfaces.

The type of generic functions is just like those of non-generic functions, with the type parameters listed first, similarly to function declarations:

```tsx
function identity<Type>(arg: Type): Type {
  return arg;
}

let myIdentity: <Type>(arg: Type) => Type = identity;

```

# ES Module Syntax

A file can declare a main export via export default:

```
// @filename: hello.ts
export default function helloWorld() {
  console.log("Hello, world!");
}
Try

```

This is then imported via:

```
import helloWorld from "./hello.js";
helloWorld();
Try

```

In addition to the default export, you can have more than one export of variables and functions via the exportby omitting default:

```
// @filename: maths.ts
export var pi = 3.14;
export let squareTwo = 1.41;
export const phi = 1.61;

export class RandomNumberGenerator {}

export function absolute(num: number) {
  if (num < 0) return num * -1;
  return num;
}
Try

```

These can be used in another file via the importsyntax:

```
import { pi, phi, absolute } from "./maths.js";

console.log(pi);
const absPhi = absolute(phi);
        const absPhi: number

```

## CommonJS Syntax

CommonJS is the format which most modules on npm are delivered in. Even if you are writing using the ES Modules syntax above, having a brief understanding of how CommonJS syntax works will help you debug easier.

### Exporting

Identifiers are exported via setting the exportsproperty on a global called module.

```
function absolute(num: number) {
  if (num < 0) return num * -1;
  return num;
}

module.exports = {
  pi: 3.14,
  squareTwo: 1.41,
  phi: 1.61,
  absolute,
};
Try

```

Then these files can be imported via a requirestatement:

```
const maths = require("./maths");
maths.pi;
      any
Try

```

Or you can simplify a bit using the destructuring feature in JavaScript:

```
const { squareTwo } = require("./maths");
squareTwo;

```
