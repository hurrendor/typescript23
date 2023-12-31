---
id: nh8b6uite0wnu04fh6yffjo
title: Features
desc: ''
updated: 1695231145632
created: 1691603907682
---
# Functions

Default values can be set for parameters.
### Return Types
Type annotation - `function returnsThang(): boolean {}`

### TypeScript keywords
* `void`  function return value tells TS to ignore
* `never` function return type
    - nothing can return or run after this function call
    - Point of no return
    - This will never be inferred, needs to be explicitly stated
    - Most common in command line code (deno) or in unit tests
    
    Outside of functions, `never` means it's an invalid type - this case shouldn't be used.

## Function Types
`type StringToNumber = (input: string) => number;`

[Parameter and Return Type Annotation Practice](https://www.learningtypescript.com/functions/secret-secrets/)


# Arrays
[Single and Multidemensional Array and Type Annotation Practice](https://www.learningtypescript.com/arrays/analyzing-dna/)

# Interfaces
A way to describe something similar to an object type. TLDR same as object typing.
Differences is how they are extended or combined
`interface NameAndPower extends JustName {}`

[Writing Interfaces - Practice](https://www.learningtypescript.com/interfaces/vacation-planning/)

## Index Signatures
Setting a 'catch-all' value
```
    interface EverythingIsANumber {
        base: 0;
        [i: string]:number;
    }
```    