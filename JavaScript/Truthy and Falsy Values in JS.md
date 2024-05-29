# Truthy and Falsy Values in JavaScript

In JavaScript, values are considered either "truthy" or "falsy" when evaluated in a Boolean context, such as in an if statement. Here is a list of all the falsy values and some common truthy values:

## Falsy Values
There are exactly 8 falsy values in JavaScript:

1. `false` - The Boolean value `false`.
2. `0` - The number zero.
3. `-0` - The number negative zero.
4. `0n` - The BigInt zero.
5. `""` - An empty string.
6. `null` - The absence of any value.
7. `undefined` - A variable that has been declared but not assigned a value.
8. `NaN` - The result of an invalid number operation (Not-a-Number).

#

## Truthy Values
All values that are not falsy are considered truthy. Here are some common examples of truthy values:

1. `true` - The Boolean value `true`.
2. Any non-zero number (e.g., 1, -1, 3.14).
3. Any non-empty string (e.g., `"hello"`, "0", `"false"`).
4. Any object (e.g., `{}`, `[]`, `function() {}`).
5. Any non-zero BigInt (e.g., `1n`, `-1n`).
6. `Infinity` and `-Infinity`.

#

## Examples in Code

Here are some examples to illustrate truthy and falsy values in JavaScript:

```javascript
if (false) {
  console.log("This will not run");
}

if (0) {
  console.log("This will not run");
}

if ("") {
  console.log("This will not run");
}

if (null) {
  console.log("This will not run");
}

if (undefined) {
  console.log("This will not run");
}

if (NaN) {
  console.log("This will not run");
}

if (true) {
  console.log("This will run");
}

if (1) {
  console.log("This will run");
}

if ("hello") {
  console.log("This will run");
}

if ({}) {
  console.log("This will run");
}

if ([]) {
  console.log("This will run");
}
```
