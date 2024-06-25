# Closures in JavaScript

A closure is a fundamental concept in JavaScript (and in many other programming languages) where an inner function has access to the outer (enclosing) function’s variables and parameters even after the outer function has finished executing. This is possible because functions in JavaScript form closures.

Closures allow functions to retain access to their lexical scope, which is the scope in which they were defined, even when they are executed outside that scope.

#

## Example Explanation
Let's look at the following example:
```javascript
(function () {
  const header = document.querySelector('h1');
  header.style.color = 'red';

  document.querySelector('body').addEventListener('click', () => {
    header.style.color = 'blue';
  });
})();
```
### Breakdown
**1. Immediately Invoked Function Expression (IIFE):**
   - The entire function is an IIFE. It runs as soon as it is defined.
   - This creates a local scope for the variables and functions defined within it, preventing them from polluting the global scope.

**2. Variable header:**
   - The header variable is defined within the IIFE and stores a reference to the element in the document.
   - Initially, the color of the header is set to red.

**3. Event Listener:**
   - An event listener is added to the <body> element. It listens for click events.
   - The callback function inside addEventListener changes the color of the header to blue when the body is clicked.

### Closure in this context
The event listener callback function forms a closure over the IIFE. This means that even though the IIFE has finished executing by the time the click event occurs, the callback function retains access to the header variable.

In other words, the closure in this example is created by the event listener callback function. Even after the IIFE has executed and its scope would normally be destroyed, the callback function retains access to the header variable. This allows the event listener to change the header’s color when the body is clicked.

#

## Key Points about Closures
1. **Lexical Scope:** Functions have access to the scope in which they were created.</br>
2. **Persistent Access:** The inner function retains access to the outer function’s variables even after the outer function has executed.

#

## Further Examples
### Example 1: Basic Closure
```javascript
function outerFunction() {
  const outerVariable = 'I am outside!';

  function innerFunction() {
    console.log(outerVariable); // The inner function has access to outerVariable
  }

  return innerFunction;
}

const myFunction = outerFunction();
myFunction(); // Output: I am outside!
```
In this example:
- innerFunction has access to outerVariable even after outerFunction has returned.
- myFunction retains access to the scope where it was created, demonstrating closure.

#

### Example 2: Closure with Parameters
```javascript
function makeCounter() {
  let count = 0;

  return function() {
    count++;
    return count;
  };
}

const counter = makeCounter();
console.log(counter()); // Output: 1
console.log(counter()); // Output: 2
console.log(counter()); // Output: 3
```
In this example:
- The inner function returned by makeCounter has access to the count variable.
- Each call to counter increments and returns the updated value of count.

#

### Example 3: Private Variables

Closures can be used to create private variables that are not accessible from the outside.
```javascript
function createPerson(name) {
  return {
    getName: function() {
      return name;
    },
    setName: function(newName) {
      name = newName;
    }
  };
}

const person = createPerson('Alice');
console.log(person.getName()); // Output: Alice
person.setName('Bob');
console.log(person.getName()); // Output: Bob
```
In this example:
- The name variable is private to the createPerson function.
- The getName and setName methods form closures over the name variable, allowing controlled access to it.

#

## Summary
- **Closure:** An inner function has access to the outer (enclosing) function’s variables even after the outer function has executed.
- **Lexical Scope:** Functions remember the scope in which they were created.
- **Use Cases:**
  - _Event Handlers:_ Retaining access to variables after the outer function has completed.
  - _Data Privacy:_ Creating private variables.
  - _Partial Applications:_ Retaining arguments for later use.
 
#
fin.
