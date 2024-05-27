# Comparison of Classes, Objects, Properties, and Methods in TypeScript

| Aspect       | Class                                       | Object                                       | Property                                  | Method                                     |
|--------------|---------------------------------------------|----------------------------------------------|-------------------------------------------|--------------------------------------------|
| **Definition** | A blueprint for creating objects.           | An instance of a class.                       | A variable that holds data within a class or object. | A function defined within a class that operates on the object's properties. |
| **Role**     | Defines the structure and behavior of objects. | Represents an entity with its own state and behavior. | Represents the data/state of an object.   | Defines actions/behavior for an object.   |
| **Nature**   | Template/blueprint for objects.             | Concrete instance with actual data.          | Data specific to an object.               | Actions that can be performed by an object. |
| **Context**  | Used to create objects.                     | Holds data and methods as defined by its class. | Data members of a class or object.        | Functions that manipulate object properties. |
| **Creation** | Defined using the `class` keyword.          | Created using the `new` keyword followed by a class constructor. | Declared within a class.                  | Declared within a class.                  |
| **Example**  | ```typescript                                | ```typescript                                | ```typescript                             | ```typescript                              |
|              | class Person {                               | const person1 = new Person("Alice", 30);     | class Car {                               | class Car {                                |
|              |     name: string;                            | console.log(person1.name); // Alice          |     make: string;                         |     make: string;                          |
|              |     age: number;                             | console.log(person1.age); // 30              |     model: string;                        |     model: string;                         |
|              |                                              | person1.greet(); // Output: Hello, my name is Alice and I am 30 years old. |     year: number;                         |     year: number;                          |
|              |     constructor(name: string, age: number) { |                                              |                                            |                                            |
|              |         this.name = name;                    |                                              |     constructor(make: string, model: string, year: number) { |     constructor(make: string, model: string, year: number) { |
|              |         this.age = age;                      |                                              |         this.make = make;                 |         this.make = make;                  |
|              |     }                                        |                                              |         this.model = model;               |         this.model = model;                |
|              |                                              |                                              |         this.year = year;                 |         this.year = year;                  |
|              |     greet(): void {                          |                                              |     }                                      |     }                                      |
|              |         console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`); |                                              |                                            |                                            |
|              |     }                                        |                                              |     drive(): void {                       |     drive(): void {                        |
|              | }                                            |                                              |         console.log(`Driving a ${this.year} ${this.make} ${this.model}`); |         console.log(`Driving a ${this.year} ${this.make} ${this.model}`); |
|              | ```                                          | ```                                          | ```                                        | ```                                        |
| **Output**   |                                              |                                              | ```typescript                             | ```typescript                              |
|              | const person1 = new Person("Alice", 30);     | const car1 = new Car("Toyota", "Corolla", 2020); | const car1 = new Car("Toyota", "Corolla", 2020); | const car1 = new Car("Toyota", "Corolla", 2020); |
|              | person1.greet(); // Hello, my name is Alice and I am 30 years old. | console.log(car1.make); // Toyota           | console.log(car1.make); // Toyota         | car1.drive(); // Driving a 2020 Toyota Corolla |
|              |                                              | console.log(car1.model); // Corolla          | console.log(car1.model); // Corolla       |                                            |
|              |                                              | console.log(car1.year); // 2020              | console.log(car1.year); // 2020           |                                            |
|              |                                              |                                              |                                            |                                            |

