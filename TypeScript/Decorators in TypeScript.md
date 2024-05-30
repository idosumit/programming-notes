# Decorators in TypScript
Decorators are a special kind of declaration in TypeScript that can be attached to a class, method, accessor, property, or parameter. They are a form of meta-programming that allows us to modify the behavior of the decorated item.

Decorators are a way to add additional functionality to existing code, and they can be used for a wide range of tasks, including logging, performance optimization, and validation. They are a feature from the ECMAScript proposal and are available as an experimental feature in TypeScript.

#

## Types of Decorators
1. Class Decorators
2. Method Decorators
3. Accessor Decorators
4. Property Decorators
5. Parameter Decorators

#

## Enabling Decorators
To use decorators, we need to enable the `experimentalDecorators` compiler option in our `tsconfig.json`:
```json
{
  "compilerOptions": {
    "experimentalDecorators": true
  }
}
```

## Detailed Examples
### 1. Class Decorators
A class decorator is applied to the class constructor. It can be used to modify or replace the class definition.
```typescript
function sealed(constructor: Function) {
    Object.seal(constructor);
    Object.seal(constructor.prototype);
}

@sealed
class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }

    greet() {
        return `Hello, ${this.greeting}`;
    }
}

const greeter = new Greeter("world");
console.log(greeter.greet()); // Output: Hello, world
```
In this example, the `@sealed` decorator seals the `Greeter` class, preventing new properties from being added to it.

#

### 2. Method Decorator
A method decorator is applied to a method's property descriptor. It can be used to modify the method's behavior.
```typescript
function enumerable(value: boolean) {
    return function (target: any, propertyKey: string, descriptor: PropertyDescriptor) {
        descriptor.enumerable = value;
    };
}

class Person {
    name: string;
    constructor(name: string) {
        this.name = name;
    }

    @enumerable(false)
    greet() {
        return `Hello, ${this.name}`;
    }
}

const person = new Person("Alice");
for (let key in person) {
    console.log(key); // 'name' (but not 'greet')
}
```
Here, the `@enumerable(false)` decorator sets the `enumerable` property of the `greet` method's descriptor to `false`, preventing it from appearing in a `for...in` loop.

#

### 3. Accessor Decorators
An accessor decorator is applied to a property accessor (getter or setter) and can be used to modify the accessor's descriptor.

```typescript
function configurable(value: boolean) {
    return function (target: any, propertyKey: string, descriptor: PropertyDescriptor) {
        descriptor.configurable = value;
    };
}

class Car {
    private _make: string;

    constructor(make: string) {
        this._make = make;
    }

    @configurable(false)
    get make() {
        return this._make;
    }
}

const car = new Car("Toyota");
console.log(car.make); // Output: Toyota
```
In this example, the `@configurable(false)` decorator sets the `configurable` property of the `make` getter's descriptor to `false`, preventing the descriptor from being changed or deleted.

#

### 4. Property Decorators
A property decorator is applied to a class property and can be used to observe or modify the property definition.
```typescript
function logProperty(target: any, key: string) {
    let value = target[key];

    const getter = () => {
        console.log(`Get: ${key} => ${value}`);
        return value;
    };

    const setter = (newVal) => {
        console.log(`Set: ${key} => ${newVal}`);
        value = newVal;
    };

    Object.defineProperty(target, key, {
        get: getter,
        set: setter,
        enumerable: true,
        configurable: true
    });
}

class Employee {
    @logProperty
    name: string;

    constructor(name: string) {
        this.name = name;
    }
}

const emp = new Employee("John");
emp.name = "Doe"; // Output: Set: name => Doe
console.log(emp.name); // Output: Get: name => Doe
```
Here, the `@logProperty` decorator logs the access and assignment to the `name` property.

#

### 5. Parameter Decorators
A parameter decorator is applied to a parameter in a class constructor or method. It can be used to observe or modify the parameter.
```typescript
function logParameter(target: any, key: string, index: number) {
    const metadataKey = `__log_${key}_parameters`;
    if (Array.isArray(target[metadataKey])) {
        target[metadataKey].push(index);
    } else {
        target[metadataKey] = [index];
    }
}

class Manager {
    greet(@logParameter message: string): string {
        return `Hello, ${message}`;
    }
}

const manager = new Manager();
manager.greet("world"); // No visible output, but the parameter is logged internally
```
In this example, the `@logParameter` decorator records the index of the parameter in a metadata key on the target method.

#

## Summary
- Decorators: A form of meta-programming in TypeScript used to annotate and modify classes, methods, accessors, properties, and parameters.
- Types of Decorators:
  * Class Decorators: Modify or replace the class constructor.
  * Method Decorators: Modify the method's property descriptor.
  * Accessor Decorators: Modify the accessor's property descriptor.
  * Property Decorators: Observe or modify the property definition.
  * Parameter Decorators: Observe or modify the method parameter.
- Usage: Decorators are applied using the @ symbol before the declaration.

#

## Practical Applications
- Logging: Automatically log method calls, property accesses, or parameter values.
- Validation: Validate method parameters or property values.
- Authorization: Check user permissions before executing methods.
- Metadata: Attach metadata to classes, methods, or properties for runtime reflection.
