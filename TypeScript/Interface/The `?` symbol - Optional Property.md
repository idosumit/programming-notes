# The `?` Symbol in TypeScript: Optional Property in an Interface
The `?` symbol in TypeScript denotes an optional property in an interface. When a property is marked as optional, it means that objects adhering to the interface can either include the property or omit it altogether. This is useful for defining flexible data structures where certain properties are not always required.

In more details, an optional property is one that can either be present or absent in the objects that implement the interface. Optional properties are useful in situations where not all properties are required for the object to be valid.

#

## Syntax
```typescript
interface InterfaceName {
    propertyName?: type;
}
```

#

## Examples
### Basic Example

```tyescript
interface User {
    id: number;
    name: string;
    email?: string; // email is optional
}

const user1: User = {
    id: 1,
    name: "Alice"
};

const user2: User = {
    id: 2,
    name: "Bob",
    email: "bob@example.com"
};

console.log(user1); // Output: { id: 1, name: 'Alice' }
console.log(user2); // Output: { id: 2, name: 'Bob', email: 'bob@example.com' }
```

In this example, the `email` property is optional, so `user1` is a valid User object even without an `email`.

#

### Optional Properties in Functions
We can define functions that accept objects with optional properties and handle those properties appropriately.
```typescript
interface Config {
    timeout?: number;
    baseURL?: string;
}

function setup(config: Config) {
    const timeout = config.timeout ?? 3000; // Default timeout is 3000 (?? is the nullish coalescing operator)
    const baseURL = config.baseURL ?? "http://localhost"; // Default baseURL
    console.log(`Config - Timeout: ${timeout}, BaseURL: ${baseURL}`);
}

setup({ timeout: 5000 }); // Output: Config - Timeout: 5000, BaseURL: http://localhost
setup({ baseURL: "http://example.com" }); // Output: Config - Timeout: 3000, BaseURL: http://example.com
setup({}); // Output: Config - Timeout: 3000, BaseURL: http://localhost
```
Here, the `setup` function can handle `Config` objects with or without the `timeout` and `baseURL` properties.

#

### Optional Properties in Union Types
When using union types in interfaces, optional properties can help define more flexible and precise types.
```typescript
interface Circle {
    kind: "circle";
    radius?: number;
}

interface Square {
    kind: "square";
    sideLength?: number;
}

type Shape = Circle | Square;

function describeShape(shape: Shape) {
    if (shape.kind === "circle") {
        console.log(`Circle with radius: ${shape.radius ?? "unknown"}`);
    } else {
        console.log(`Square with side length: ${shape.sideLength ?? "unknown"}`);
    }
}

describeShape({ kind: "circle", radius: 10 }); // Output: Circle with radius: 10
describeShape({ kind: "square" }); // Output: Square with side length: unknown
```
In this example, the `radius` and `sideLength` properties are optional, allowing for more flexible shape definitions.

#

### Optional Properties and Default Values
We can use the nullish coalescing operator (`??`) or logical OR (`||`) to provide default values for optional properties when they are not provided.
```typescript
interface Settings {
    theme?: string;
    layout?: string;
}

function applySettings(settings: Settings) {
    const theme = settings.theme ?? "dark"; // Default to "dark" if theme is not provided
    const layout = settings.layout || "grid"; // Default to "grid" if layout is not provided
    console.log(`Applied settings - Theme: ${theme}, Layout: ${layout}`);
}

applySettings({ theme: "light" }); // Output: Applied settings - Theme: light, Layout: grid
applySettings({}); // Output: Applied settings - Theme: dark, Layout: grid
```

#

## Summary
- Optional Properties: Denoted by `?`, they allow properties to be omitted in objects implementing an interface.
- Syntax: `propertyName?: type;`
- Use Cases: Flexible data structures, functions with optional parameters, and union types.
- Handling Optional Properties: Use default values with `??` or `||` to handle cases where optional properties are not provided.
