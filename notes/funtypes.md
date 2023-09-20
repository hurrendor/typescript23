---
id: i4v85k6s6w898ms2cu6t04g
title: Funtypes
desc: ''
updated: 1695232430980
created: 1691613659535
---
# 1. Type Modifiers

## Type Assertions
**Most** of the time, typescript assertions are the wrong strategy.

Format: value as type. ex: `(foo as string)`

## Keyof Types
Given
```
    interface catValues = { fur: boolean; name: string; }
```
Take the properties defined in an interface or type and take those values into another area.

`function thang(foo: keyof catValues)` 


## Typeof Types
Takes the typing defined elsewhere in an interface or type into another area that's expressed
`function thang(foo: typeof catValues)` 

**Can be chained!**
`fn foo(bar: keyof typeof catValues)`

Slide: 70
[Type Modifier Practice](https://www.learningtypescript.com/type-modifiers/modifiers-of-the-types/)

### Type Predicate
If the checked thing is true, then property values will be applied
ex: `function checkThing(value: unknown): value is { happy?: boolean} {}`

Assertion can be used to throw an error if the following type is not true
`fn assertIsParsedValue(value: unknown): asserts value is ParsedValue`

# 2. Generics
Like `T`
Signifies that every time the construct is used, the value type will be consistent but could be different. Great for identifying when the value passed through will be unknown.
Syntax uses angle brackets to indicate that it is a **generic typed parameter**
`function identity<T>` or `function identity<ThisIsAGenericTypeName>`
The naming doesn't matter too much but it's best convention to use one consistently or uppercasing.

## Generic Interfaces
`interface Box<T> { value: T }` 
When being extended, will set the type to whatever value is set.

### Defaults
`interface Box<T = string> { value: T }`

## Parameter Type Defaults & Keyof Types
[Generics Practice](https://www.learningtypescript.com/generics/hidash/)
```
function get<T, Key extends keyof T>( 
        container: T, 
        key: Key
    ){
        return container[key]
}
```
This denotes that the Key provided needs to be a key present from T. Allows the ability to change the function return type based on the type of parameters. If there's more than one key defined in the generic value being passed in, the key value could be any of the types defined.


Generics with arrays/objects being passed in --- TODO: Come back to, this is a little weird
`function pick<T, Key extends keyof T>(val: T, keys: Key[])`

# 3. Type Operations
Taking types and making new types out of them

## Mapped Types
```
type NullableBeing = {
    [K in keyof Being]: Being[K] | null;
}
```
is equivalent to
```
interface NullableBeingManual {
    name: string | null;
    power: number | null;
}
```

The first is more powerfull, but can also be a visual code barrier of entry to newer or less experience developers.

## Modifying Mapped Types
**Nullable** is applied to the type
`[Key in keyof Being]?: Being[K] | null`

## Generic Mapped Types
```
type NullableBeing = {
    [K in keyof Being]: Being[K] | null;
}
```
equivalent to
```
interface NullableBeingManual {
    name: string | null;
    power: number | null;
}
```
Can create lack of run-time logic by automating typing setup. Also, a nightmare to read through.

## Conditional Types (slide 82)
Conditional types cannot be used to set a value in a variable, but can be used to set a type on the variable.
A type can be set to the resulting value of type, and then applied to a variable.

## Inferred Types (slide 83)
using the `infer` keyword
` type MyAwaited<T> = T extends Promise<infer U> ? U : never;`

