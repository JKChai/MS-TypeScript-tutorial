# MS-TypeScript-tutorial

Completing a tutorial on TypeScript with Microsoft education: https://docs.microsoft.com/en-us/learn/modules/typescript-get-started/6-typescript-project

# Files info

* `module01.ts` - first exercise for the tutorial
* `module01.html` - html component to visualize onto web browser
* `tsconfig.json` - defines the TypeScript project settings, such as the compiler options & files to be included

# Requirements

* IDE (VS CODE)
* `node.JS` (specifically `npm`)
* TypeScript transpiler (`tsc`)

# TO Note

> Some key concepts to understand

* `tsc --init` create `tsconfig.json` file
* `${ expr }` - embedded expressions
* `any` - type that can repsrent any JavaScript value with no constraints. This type has a cost of losing type safety
* `unknown` - similar to `any` type but restraints from being constructed and called in which properties cannot be accessed, which is to restraint interaction invoking compile errors
* `typeof` - to check on data type of a variable mainly for primitive types
* `instanceof` - to check the type of class
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
* Named functions (To reuse the functions) & Anonymous function (To assign function expression to a variable) & Arrow functions 
* Type of Parameters in function: Required, Optional, Default, Rest
* Function Type Inference - names of the function parameters do not need to match those in the function type; name are ignored when checking if 2 function types are compatible
```TS
interface Calculator {
    (x: number, y: number): number;
}

// Three of the functions below are identical
let addNumbers: Calculator = (x: number, y: number): number => x + y;
let addNumbers: Calculator = (number1: number, number2: number): number => number1 + number2;
let addNumbers: Calculator = (num1, num2) => num1 + num2;
```

## Keyword

* Declaring Types
* Static Type Checking
* Type Assertions
* Type Guards
* Type Safety
* Duck Typing
* Structural Subtyping
* Deconstructed Object Parameters
* encapsulates

## Primitive types

> Also known as literal types

* boolean
* number
* bigint
* string
* function
* symbol
* object
* undefined
 
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

## class

* properties
* constructor
* accessors
* methods

### Access Modifier

* `public` - by default
* `private` - cannot be accessed from outside of its containing class
* `protected` - similar to `private` but can be accessed with deriving classses

#### NOTE from MS
>  TypeScript is a structural type system. When you compare two different types, regardless of where they came from, if the types of all members are compatible, then we say the types themselves are compatible. However, when comparing types that have private and protected members, these types are treated differently. For two types to be considered compatible, if one of them has a private member, then the other must have a private member that originated in the same declaration. The same applies to protected members.

### Define Static Properties

* Instance properties - they are instantiated and called on each instance of the class object
* Static property - properties and methods are shared by all instances of a class

### Extend a class using inheritance

* subclass
* base class (also known as superclasses or parent classes)
* overriden - create same name in subclass from the base class but have different functionalities
* implements - use it with class to implement the object shape; it only provides the contract of the shape that the class has to follow. The difference between `extend` is that `extend` inherit all the properties and does not required implementation, think of it as do not have to rewrite the shape objects again.

## Generics

> code templates defined that can be reused throughout the codebase
>
> Create generic functions when your code is a function or class that:
> * works with a variety of data types
> * Uses that data type in serveral places
>
> Generics can:
> * Provide more flexibility when working with types
> * Enable code reuse
> * Reduce the need to use the `any` type
>
> Generics define one or more type variables to identify the type or types that you will pass to the component, enclosed in angle brackets (< >). (You'll also see type variables referred to as type parameters or generic parameters.) In the example above, the type variable in the function is called <T>. T is a commonly used name for a generic, but you can name it however you wish.
>

### Multiple Type Variables

> `identity` function below accepts 2 parameters & returns the value parameter

```TS
function identity<T, U> (value: T, message: U) : T {
    console.log(message);
    return value
}

let returnNumber = identity<number, string>(100, 'Hello!');
let returnString = identity<string, string>('100', 'Hola!');
let returnBoolean = identity<boolean, string>(true, 'Bonjour!');

returnNumber = returnNumber * 100;   // OK
returnString = returnString * 100;   // Error: Type 'number' not assignable to type 'string'
returnBoolean = returnBoolean * 100; // Error: Type 'number' not assignable to type 'boolean'
```

> `generic constraint`