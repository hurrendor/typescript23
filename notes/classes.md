---
id: phvpuu4c4mmsq4n2dv42nii
title: Classes
desc: ''
updated: 1695231233682
created: 1691613603258
---
TS Config Property - useDefinedProperty **<--- clarify**

Classes can implement interfaces
`class Person implements Being {}`
Only provides errors if incorrect typing has been provided
The values from Being can be initialized in Person without needing to re-write the typing, and the pre-stated typing is pulled over

## Soft Privacy
* `public` - default value
* `protected` - only accessible within class and subclasses
* `private` only accessible within specified class

* `abstract` - class type doesn't allow a constructor, needs to be implemented by extension into another class. 
    * **Edge Case**
        If an abstract class declares a property that is not initiated in the extended class, the value will not be set.

[Describing Members with Annotations Practice](https://www.learningtypescript.com/classes/classifying-creatures/)

##### Side Note: JavaScript has just introduced a runtime feature of ``#`` - indicating private. This is respected by TypeScript

Adding this feature requires adding updates to the tsconfig file compiler options to signify what JS version is being used
```
"compilerOptions": {
    "target": "esnext"
},
```
