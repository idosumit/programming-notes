# Nullish Coalescing Operator (`??`)
The nullish coalescing operator is a logical operator that returns its right-hand operand when its left-hand operand is `null` or `undefined`, and otherwise returns its left-hand operand.

## Syntax
```javascript
const result = value ?? defaultValue;
```

## Usage
The nullish coalescing operator is useful for providing default values while distinguishing between `null`/`undefined` and other falsy values (like `0`, `""`, `false`, etc.). This is particularly helpful in situations where we want to avoid mistakenly treating other falsy values as needing the default.
> [Truthy and Falsy Values Notes](https://github.com/idosumit/programming-notes/blob/main/JavaScript/Truthy%20and%20Falsy%20Values%20in%20JS.md)

## Detailed Examples
### Providing Default Values
In the given example:
```javascript
const timeout = config.timeout ?? 3000;
```
This means:
- If `config.timeout` is `null` or `undefined`, `timeout` will be assigned the value `3000`.
- If `config.timeout` is any other value (including `0`, `false`, `""`, etc.), timeout will be assigned the value of `config.timeout`.

#

### Nullish Coalescing with `null` and `undefined`
```javascript
const config1 = { timeout: undefined };
const timeout1 = config1.timeout ?? 3000;
console.log(timeout1); // Output: 3000

const config2 = { timeout: null };
const timeout2 = config2.timeout ?? 3000;
console.log(timeout2); // Output: 3000
```

#

### Nullish Coalescing with Other Falsy Values
```javascript
const config3 = { timeout: 0 };
const timeout3 = config3.timeout ?? 3000;
console.log(timeout3); // Output: 0 (not 3000, because 0 is not null or undefined)

const config4 = { timeout: false };
const timeout4 = config4.timeout ?? 3000;
console.log(timeout4); // Output: false (not 3000, because false is not null or undefined)

const config5 = { timeout: "" };
const timeout5 = config5.timeout ?? 3000;
console.log(timeout5); // Output: "" (not 3000, because "" is not null or undefined)
```

#

## Comparison with Logical OR (`||`)
The logical OR (`||`) operator can also be used to provide default values, but it treats all falsy values (like `0`, `false`, `""`, etc.) as needing the default, not just null or undefined.
> [Notes on logican OR (`||`) and short circuiting in JavaScript](https://github.com/idosumit/programming-notes/blob/main/JavaScript/Short%20Circuiting%20in%20JS.md)

### Example
```javascript
const config = { timeout: 0 };
const timeoutWithOR = config.timeout || 3000;
console.log(timeoutWithOR); // Output: 3000 (0 is considered falsy and therefore returns the default)

const timeoutWithNullish = config.timeout ?? 3000;
console.log(timeoutWithNullish); // Output: 0 (nullish coalescing only considers null or undefined)
```

#

## Summary
- **Nullish Coalescing Operator (`??`)**: Used to provide a default value when the left-hand operand is `null` or `undefined`.
- **Syntax**: `const result = value ?? defaultValue;`
- **Purpose**: Distinguishes between `null`/`undefined` and other falsy values, providing a default only when necessary.
- **Comparison with `||`**: The logical OR operator treats all falsy values as needing the default, while `??` only considers `null` and `undefined`.
