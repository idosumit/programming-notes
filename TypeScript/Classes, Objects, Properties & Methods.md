# Comparison of Classes, Objects, Properties, and Methods in TypeScript

## Table of Contents
* [Comparison](#comparison)
* [Detailed Examples](#detailed-examples)
   * [Class](#class)
   * [Object](#object)
      * [1. Object Literal](#1-object-literal)
      * [2. Using Interfaces](#2-using-interfaces)
      * [3. Using Classes](#3-using-classes)
      * [4. Using Object.create](#4-using-object.create)
      * [5. Using Type Aliases](#5-using-type-aliases)
      * [6. Using Constructors with Interfaces](#6-using-constructors-with-interfaces)
      * [7. Using Factory Functions](#7-using-factory-functions)
      * [8. Using Enums](#8-using-enums)
      * [9. Using Mapped Types](#9-using-mapped-types)
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

#

## Detailed Examples
### Class
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

#

### Object

#### 1. Object Literal
The most straightforward way to create an object is using an object literal.

```typescript
const person = {
    name: "John Doe",
    age: 25,
    isStudent: true
};
```

#### 2. Using Interfaces
You can define the shape of an object using an interface and then create an object that adheres to that interface.
```typescript
interface Person {
    name: string;
    age: number;
    isStudent: boolean;
}

const person: Person = {
    name: "John Doe",
    age: 25,
    isStudent: true
};
```

#### 3. Using Classes
You can define a class and create an instance of that class.

```typescript
class Person {
    name: string;
    age: number;
    isStudent: boolean;

    constructor(name: string, age: number, isStudent: boolean) {
        this.name = name;
        this.age = age;
        this.isStudent = isStudent;
    }
}

const person = new Person("John Doe", 25, true);
```

#### 4. Using Object.create
You can create an object with a specified prototype using Object.create.

```typescript
const proto = {
    greet() {
        console.log("Hello!");
    }
};

const person = Object.create(proto);
person.name = "John Doe";
person.age = 25;
person.isStudent = true;
```

#### 5. Using Type Aliases
Similar to interfaces, you can use type aliases to define the shape of an object.
```typescript
type Person = {
    name: string;
    age: number;
    isStudent: boolean;
};

const person: Person = {
    name: "John Doe",
    age: 25,
    isStudent: true
};
```

#### 6. Using Constructors with Interfaces
You can combine constructors and interfaces to create objects.

```typescript
interface Person {
    name: string;
    age: number;
    isStudent: boolean;
}

function createPerson(name: string, age: number, isStudent: boolean): Person {
    return { name, age, isStudent };
}

const person = createPerson("John Doe", 25, true);
```

#### 7. Using Factory Functions
You can use factory functions to create objects.

```typescript
function createPerson(name: string, age: number, isStudent: boolean) {
    return {
        name,
        age,
        isStudent
    };
}

const person = createPerson("John Doe", 25, true);
```

#### 8. Using Enums
You can use enums to create objects with predefined values.

```typescript
enum StudentStatus {
    Active,
    Inactive,
    Graduated
}

const person = {
    name: "John Doe",
    age: 25,
    status: StudentStatus.Active
};
```

#### 9. Using Mapped Types
You can use mapped types to create objects dynamically.

```typescript
type Keys = "name" | "age" | "isStudent";

type Person = {
    [K in Keys]: string | number | boolean;
};

const person: Person = {
    name: "John Doe",
    age: 25,
    isStudent: true
};
```

#

### Property
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

#

### Method
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

#

## Table of Contents
* [Comparison](#comparison)
* [Detailed Examples](#detailed-examples)
   * [Class](#class)
   * [Object](#object)
      * [1. Object Literal](#1-object-literal)
      * [2. Using Interfaces](#2-using-interfaces)
      * [3. Using Classes](#3-using-classes)
      * [4. Using Object.create](#4-using-object.create)
      * [5. Using Type Aliases](#5-using-type-aliases)
      * [6. Using Constructors with Interfaces](#6-using-constructors-with-interfaces)
      * [7. Using Factory Functions](#7-using-factory-functions)
      * [8. Using Enums](#8-using-enums)
      * [9. Using Mapped Types](#9-using-mapped-types)
   * [Property](#property)
   * [Method](#method)
