# Comparison of Classes, Objects, Properties, and Methods in TypeScript

### Table of Contents
* [Comparison](#comparison)
* [Detailed Examples](#detailed-examples)
   * [Class](#class)
   * [Object](#object)
   * [Property](#property)
   * [Method](#method)

#

### Comparison
| Aspect      | Class                                      | Object                                     | Property                                | Method                                 |
|-------------|--------------------------------------------|--------------------------------------------|-----------------------------------------|----------------------------------------|
| **Definition** | A blueprint for creating objects.          | An instance of a class.                     | A variable that holds data within a class or object. | A function defined within a class that operates on the object's properties. |
| **Role**    | Defines the structure and behavior of objects. | Represents an entity with its own state and behavior. | Represents the data/state of an object. | Defines actions/behavior for an object. |
| **Nature**  | Template/blueprint for objects.            | Concrete instance with actual data.        | Data specific to an object.             | Actions that can be performed by an object. |
| **Context** | Used to create objects.                    | Holds data and methods as defined by its class. | Data members of a class or object.      | Functions that manipulate object properties. |
| **Creation**| Defined using the `class` keyword.         | Created using the `new` keyword followed by a class constructor. | Declared within a class.                | Declared within a class.               |
| **Example** | `class Person { ... }`                     | `const person1 = new Person("Alice", 30);` | `person1.name`                          | `person1.greet()`                      |

### Detailed Examples

#### Class
```typescript
class Person {
    // Properties
    name: string;
    age: number;

    // Constructor
    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }

    // Method
    greet(): void {
        console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
    }
}
```
#### Object
```typescript
// Creating an object from the class
const person1 = new Person("Alice", 30);

// Accessing object properties
console.log(person1.name); // Output: Alice
console.log(person1.age);  // Output: 30

// Calling a method on the object
person1.greet(); // Output: Hello, my name is Alice and I am 30 years old.
```
#### Property
```typescript
class Car {
    // Properties
    make: string;
    model: string;
    year: number;

    constructor(make: string, model: string, year: number) {
        this.make = make;
        this.model = model;
        this.year = year;
    }
}

// Creating an object from the class
const car1 = new Car("Toyota", "Corolla", 2020);

// Accessing object properties
console.log(car1.make); // Output: Toyota
console.log(car1.model); // Output: Corolla
console.log(car1.year);  // Output: 2020
```
#### Method
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

    // Method defined within the class
    drive(): void {
        console.log(`Driving a ${this.year} ${this.make} ${this.model}`);
    }
}

// Creating an object from the class
const car1 = new Car("Toyota", "Corolla", 2020);

// Calling a method on the object
car1.drive(); // Output: Driving a 2020 Toyota Corolla
```
### Table of Contents
* [Comparison](#comparison)
* [Detailed Examples](#detailed-examples)
   * [Class](#class)
   * [Object](#object)
   * [Property](#property)
   * [Method](#method)
