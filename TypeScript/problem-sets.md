# TypeScript Problem Sets
As of my progress as [follows](https://roadmap.sh/typescript):

<img src = "https://github.com/idosumit/programming-notes/assets/104295716/e305a414-dd7c-44a5-bb19-46171cf7a401" width = '700'>

#

## Problem Set 1: Function Declarations and Arrow Functions

**Problem:**
Define a function `add` in two ways:
1. Using a normal function declaration.
2. Using an arrow function.

Both functions should take two parameters of type `number` and return their sum.

<details>
<summary>Solution</summary>

```typescript
// Normal function declaration
function add(a: number, b: number): number {
    return a + b;
}

// Arrow function
const add = (a: number, b: number): number => {
    return a + b;
}
```
</details>

## Problem Set 2: Tuples
**Problem:**
Define a tuple type PersonTuple that includes a string for the name, a number for the age, and a boolean for active status. Then, create a variable person of this type with appropriate values.

<details>
<summary>Solution</summary>

```typescript
// Tuple type definition
type PersonTuple = [string, number, boolean];

// Creating a tuple variable
let person: PersonTuple = ["John Doe", 30, true];
```
</details>

## Problem Set 3: Union Types
**Problem:**
Define a union type Id that can be either a number or a string. Create a function printId that takes a parameter of type Id and logs its type. If the Id is a number, it should log "number", and if it's a string, it should log "string".

<details>
<summary>Solution</summary>
  
```typescript
type Id = number | string;

function printId(id: Id): void {
    if (typeof id === "number") {
        console.log("number");
    } else {
        console.log("string");
    }
}

// Example usage
printId(42);       // Output: number
printId("abc123"); // Output: string
```
</details>

## Problem Set 4: Null and Undefined
**Problem:**
Create a function printValue that takes a parameter of type string | null | undefined. The function should log:

- "Value is a string" if the value is a string.
- "Value is null" if the value is null.
- "Value is undefined" if the value is undefined.

<details>
<summary>Solution</summary>
  
```typescript
function printValue(value: string | null | undefined): void {
    if (value === null) {
        console.log("Value is null");
    } else if (value is undefined) {
        console.log("Value is undefined");
    } else {
        console.log("Value is a string");
    }
}

// Example usage
printValue("Hello"); // Output: Value is a string
printValue(null);    // Output: Value is null
printValue(undefined); // Output: Value is undefined
```
</details>

## Problem Set 5: Classes and Objects
**Problem:**
Define a class Car with properties make (string), model (string), and year (number). Add a method drive that logs a message containing the car's make, model, and year. Then, create an instance of Car and call the drive method.

<details>
<summary>Solution</summary>

```typescript
class Car {
    make: string;
    model: string;
    year: number;

    constructor(make: string, model: string, year: number) {
        this.make = make;
        this.model = model;
        this.year = year;
    }

    drive(): void {
        console.log(`Driving a ${this.year} ${this.make} ${this.model}`);
    }
}

// Creating an instance
const myCar = new Car("Toyota", "Corolla", 2020);
myCar.drive(); // Output: Driving a 2020 Toyota Corolla
```
</details>

## Problem Set 6: Type Assertions
**Problem:**
Define a variable value of type any and assign it a string. Use type assertions to get the length of the string and log it.

<details>
<summary>Solution</summary>

```typescript
let value: any = "This is a string";
let strLength: number = (value as string).length;
console.log(strLength); // Output: 16

// Or using angle-bracket syntax
let strLengthAlt: number = (<string>value).length;
console.log(strLengthAlt); // Output: 16
```
</details>

## Problem Set 7: Enums
**Problem:**
Define a string enum Direction with values Up, Down, Left, and Right. Create a function move that takes a parameter of type Direction and logs the direction.

<details>
<summary>Solution</summary>

```typescript
enum Direction {
    Up = "UP",
    Down = "DOWN",
    Left = "LEFT",
    Right = "RIGHT"
}

function move(direction: Direction): void {
    console.log(`Moving ${direction}`);
}

// Example usage
move(Direction.Up);    // Output: Moving UP
move(Direction.Down);  // Output: Moving DOWN
move(Direction.Left);  // Output: Moving LEFT
move(Direction.Right); // Output: Moving RIGHT
```
</details>

## Problem Set 8: Object Types
**Problem:**
Define an object type Point with properties x (number) and y (number). Create a function printCoord that takes a parameter of type Point and logs the coordinates.

<details>
<summary>Solution</summary>

```typescript
type Point = {
    x: number;
    y: number;
};

function printCoord(pt: Point): void {
    console.log("The coordinate's x value is " + pt.x);
    console.log("The coordinate's y value is " + pt.y);
}

// Example usage
printCoord({ x: 3, y: 7 }); // Output: The coordinate's x value is 3
                           //         The coordinate's y value is 7
```
</details>
