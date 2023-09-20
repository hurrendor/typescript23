---
id: 4hrs5cop4hpj0y7v5xak5ys
title: Foundations
desc: ''
updated: 1695227724857
created: 1691604451959
---
## Variables
TS also works with type inference - if a var is set to a string initially and later to a number, squigglies may appear.
If a value is unset until later, it becomes an '**evolving any**'

## Typing Types
* `any` - YOLO. Holds any of the options
* `unknown` - we don't know this
* `void` - Nothing is returned from this
* `undefined` - A value has not been set

## 7 Primitive data types (for TS)
- null
- undefined
- boolean
- string
- number
- bigint //0n, 4n..
- symbol //Symbol(), Symbol("hi")

## When to USE TypeScript
> Use TypeScript as little as possible. 

The more complex your code is and tight the restrictions are, the harder it is to use moving forward.
> Only add a ts annotation if it's telling ts something new.

In handling `const`, if the value is set then it refers to the exact value, it will never change. If a type is set, it creates a less exact/specific value.

**If ts can't infer a type, give it a type!**

VSCode: Compare active file with from Command Palette (cmd + shift + p)


## Unions and Literals
Narrowing and widening types

### Union typing 
ex: `let clown = string | number` - this value can be either or. Any following functionality that works for both value types is allowed. 
"Fun fact" - the types are called *constituents*

### Narrowing
When a value is specified with a wider type like a union type, type checking will allow more specific functionalities to apply, ie a string function that isn't available for a number type
ex: 
```
    let clown = Math.random() ? "heads" : 0
    if (typeof clown === "string") { clown.toUpperCase() }
```
### Literals
Values can be set to SPECIFIC strings, *literally* the value provided.
`let foo: "SEATTLE"` is of type string literal "SEATTLE"

#### Twoslash comment (VSCode Package - Twoslash Query Command)
`// ^?` -- will show typing on ts playground, maybe other places?

### Objects

#### Object-type Annotations
Empty object is just setting to an empty object
`let cat: {}`

When setting properties, it is **best practice** to use semi-colons to separate the definitions. The usage of commas indicates that a specification should be sequential.

**Constraint**: Typescript only allows properties/methods that it knows exists. If something is not initialized yet, it will trigger an error.

Properties of an object in typescript can be updated,even if the var is a `const`. Adding `as const` prevents property changes in the future.

#### TypeScript Mentality: 
> Set one instantiation of a variable to be the source of truth instead of adding various properties later on.

### Object Type Aliases
```
type UOMListing = { name: string; guid: number}
var foo = UOMListing;
```
Optional properties specified default to having union typing of `specifiedType | undefined`
Can override with `'exactOptionalPropertyTypes': true` in `tsconfig`    

### Discriminated Type Unions
If the two unioned items are objects with a common property name, this can be used as a discriminant to separate the two items.


#### Extending Object Typing
`type NameAndPower = JustName & { someProperty: overrideValue }` - this shows extending the properties of NameAndPower with JustName. Same in interfaces as `interface NameAndPower extends JustName {}`

Best practice is deciding on one use case and keeping it consistent. There are edge cases for either interface or object type casing though.