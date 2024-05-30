# Type Unions in TypeScript

Type unions in TypeScript allow us to define a variable, parameter, or return type that can be one of several specified types. This feature provides flexibility while maintaining type safety, ensuring that the variable can be one of the defined types but nothing else.

Union types are particularly useful when a variable or function can operate on multiple types of data. This can be common in scenarios like handling different kinds of user inputs, API responses, or flexible function arguments.

#

## Syntax
The syntax for defining a union type uses the vertical bar (|) to separate the types.
```typescript
type UnionType = Type1 | Type2 | Type3;
```

#

## Examples
### Basic Example
```typescript
let value: number | string;

value = 42;       // Valid
value = "hello";  // Valid
value = true;     // Error: Type 'boolean' is not assignable to type 'number | string'.
```

#

### Function Paramters
A function that accepts a parameter of a union type.
```typescript
function printId(id: number | string): void {
    console.log(`ID: ${id}`);
}

printId(101);           // Output: ID: 101
printId("A123");        // Output: ID: A123
printId(true);          // Error: Argument of type 'boolean' is not assignable to parameter of type 'number | string'.
```

#

### Union Types with Arrays
```typescript
let mixedArray: (number | string)[];

mixedArray = [1, "two", 3, "four"];  // Valid
mixedArray = [1, 2, true];           // Error: Type 'boolean' is not assignable to type 'number | string'.
```

#

### Type Guards
To perform operations safely on union types, we often need to use type guards. Type guards help narrow down the type within a specific block of code.
```typescript
function printValue(value: number | string): void {
    if (typeof value === "number") {
        console.log(`Number: ${value}`);
    } else {
        console.log(`String: ${value}`);
    }
}

printValue(123);        // Output: Number: 123
printValue("Hello");    // Output: String: Hello
```

#

### Union Types in Interfaces
```typescript
interface Shape {
  kind: "circle" | "square";
  radius?: number;
  sideLength?: number;
}

const getArea = (shape: Shape): number => {
  if (shape.kind === "circle") {
    return Math.PI * shape.radius! ** 2;
  } else return shape.sideLength! ** 2;
};

// const circle: Shape = { kind: "circle", radius: 4 };

const circle1Area = getArea({ kind: "circle", radius: 5 });
console.log(circle1Area);

const square1Area = getArea({ kind: "square", sideLength: 5 });
console.log(`Square 1's area is ${square1Area}.`);

console.log(typeof circle);
console.log(getArea(circle));
```

#

### Complex Example: Handling Different Response Types
Let's consider a function that can return either a success result or an error result:
```typescript
interface SuccessResponse {
  status: "success";
  data: string;
}

interface ErrorResponse {
  status: "error";
  error: string;
}

type AnswerResponse = SuccessResponse | ErrorResponse;

const fnForResponse = (response: AnswerResponse): void => {
  if (response.status === "success") {
    console.log(`Response data: ${response.data}`);
  } else console.log(`Error: ${response.error}`);
};

const successfulResponse: SuccessResponse = {
  status: "success",
  data: "This was a successful response.",
};

const unsuccessfulResponse: ErrorResponse = {
  status: "error",
  error: "Error 44: Chimp detected.",
};

fnForResponse(successfulResponse);
fnForResponse(unsuccessfulResponse);
```

#

## Summary
- **Definition**: Union types allow a variable or function parameter to be one of several specified types.
- **Syntax**: Use the vertical bar (`|`) to separate the types.
- **Flexibility with Safety**: Union types provide flexibility while maintaining type safety by restricting the types to the specified union.
- **Type Guards**: Use type guards to safely perform operations on union types.
- **Usage Scenarios**: Union types are useful for handling multiple input types, flexible function parameters, and varying response types.

