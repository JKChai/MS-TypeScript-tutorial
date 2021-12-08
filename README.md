# MS-TypeScript-tutorial
Completing a tutorial on TypeScript with Microsoft education: https://docs.microsoft.com/en-us/learn/modules/typescript-get-started/6-typescript-project

# Files info

* `module01.ts` - first exercise for the tutorial
* `module01.html` - html component to visualize onto web browser
* `tsconfig.json` - defines the TypeScript project settings, such as the compiler options & files to be included

# Requirements

* an IDE (VS CODE)
* `node.JS` (specifically `npm`)
* TypeScript transpiler (`tsc`)

# TO Note

> Some key concepts to understand

* `tsc --init` create `tsconfig.json` file
* `${ expr }` - embedded expressions
* `any` - type that can repsrent any JavaScript value with no constraints. This type has a cost of losing type safety
* `unknown` - similar to `any` type but restraints from being constructed and called in which properties cannot be accessed, which is to restraint interaction invoking compile errors
* `typeof` - to check on data type of a variable
* narrowing - process of going from an infinite number of potential cases to a smaller, finite number of potential cases
* `structural type system` - TypeScript only takes into account the members on the type when comparing types
* `?` operator - Have 3 main uses
> First use: Ternary Operator 
```JS
// Condition ? True : False
const something = what === 'True' ? 'True' : 'False';

// If Else
let status;
if( what === 'True'){
    status = 'True'
}
else{
    status = 'False'
}
```
> 2nd use: Optional Chaining
```JS
const user = {
    name: 'Nishant',
    age: 24
}

user.write?.salary();
// property salary will return as `undefined` instead of throwing error
```
> 3rd use: Nullish Coalescing
```JS
// allow 0 & '' empty string to pass
// where JavaScript usually define this as undefined or null 
// hence code below will return the specific values
const value1 = 0 ?? 'default string';
console.log(value1);
> 0

const value2 = '' ?? 1000;
console.log(value2);
> ''
```
* `interface` - use to describe an object, naming and parameterizing the object's types, and to compose existing named object types into new ones
* `type` alias VS `interface` - differences is that type alias cannot be reopened to add new properties whereas an interface is always extendable
* A type alias is better if you want to use unions or tuples.
* `interface` name (the identifier) by convention is in PascalCase
* Named functions & Anonymous function & Arrow functionscd 
* Type of Parameters in function: Required, Optional, Default, Rest

## Keyword

* Declaring Types
* Static Type Checking
* Type Assertions
* Type Guards
* Type Safety
* Duck Typing
* Structural Subtyping
* Deconstructed Object Parameters

## Primitive types

> Also known as literal types

* boolean
* number
* bigint
* string
 
## Union Types

Notice that `:` is used for assigning types & `|` is pipe acting as union

```TS
let multiType: number | boolean;
multiType = 20;         //* Valid
multiType = true;       //* Valid
multiType = "twenty";   //* Invalid
```

## Intersection Types

Combine 2 or more types with `&` operand and is mostly used with `interface`

## Collection Types

### Arrays

> Arrays can be defined in 2 ways

```TS
// 1st method: type[]
let list: number[] = [1,2,3];

// 2nd method: Array<type>
let list: Array<number> = [1,2,3];
```

### Tuples

> To carry mixed types

`variableName: [type, type, ...]`

## interface

> The shape of the object can be extended `extend`
> 
> can create indexable types

