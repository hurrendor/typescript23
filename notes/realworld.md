---
id: mim3tgsd1do3a7gpjef96af
title: Realworld
desc: ''
updated: 1695233178206
created: 1691613690495
---
# Declarations
## Declaring Variables
`declare const foo: boolean;`
The `declare` keyword claims the first usage of the variable. Usually used to declare functions, it can be used to describe types or values accessed by dotted notation.

### Global Namespace / Global Closure
`declare global {}`
Every file will have the types defined within. To use the types, the file in question needs to have an `export` set up

## Augmenting the Window
declaring a global namespace can also hold the `interface Window{}`
Everything defined in here will be merged with the existing Window interface. It's not explicitly stated, but that's what is happening.

## Augmenting Globals
`global stuff` //TODO: Come back to this section for notes as well

example:

```
 declare global {
    interface Window {
        passports: Passports;
    }
}
```

Global interface, using a generic value to pass through.
Just to kid around, use `smoosh()`
[JavaScript's 'smooshgate'](https://developer.chrome.com/blog/smooshgate/)




# Working in the IDE (Visual Studio Code)
## Forgetting Types
`.at` and right clicking will show options to show type or source

## Find All References
Goes to all locations used but also likely where it was defined.

## Rename
VSCode --> Rename Symbol can show all the places it will be renamed before it automatically refactors.
