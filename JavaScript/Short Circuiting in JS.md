# Short Circuiting in JavaScript

## Summary:
1. Short circuiting is an even better way to initialize values than ternary operator or if/else statements. HOWEVER, if our initial number is 0, short circuiting won't work.

2. **IMPORTANT**: The OR (`||`) operator will return the first truthy value of all the operands, or simply the last value if all of them are falsy. On the other hand, the AND (`&&`) operator will return the first falsy value or the last value if all of them are truthy. And as for practical applications, we can use the OR operator to set default values, and we can use the AND operator to execute code in the second operand if the first one is true.
   > [Truthy and Falsy Values Notes](https://github.com/idosumit/programming-notes/blob/main/JavaScript/Truthy%20and%20Falsy%20Values%20in%20JS.md)
#

## The OR Operator (`||`)

```javascript
console.log(3 || 'Barkley'); // 3 is truthy, so returns 3
console.log('' || 'Charles'); // '' is falsy, so returns 'Charles'
console.log(true || 0); // true is truthy, so returns true
console.log(undefined || null); // undefined. undefined is falsy so it doesn't reach null
console.log(undefined || 0 || '' || 'Hello' || 23 || null); // 'hello' is the 1st truthy value, so returns 'hello'
```

**The `||` operator can make our code more compact.**

Example:
Let's suppose our original code is the following:

```javascript
const restaurant = {
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  order: function (starterIndex, mainIndex) {
    return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]];
  },
  orderPasta: function (ing1, ing2, ing3) {
    console.log(`Here is your pasta with ${ing1}, ${ing2}, and ${ing3}.`);
  },
  orderPizza: function (mainIngredient, ...otherIngredients) {
    console.log(mainIngredient);
    console.log(otherIngredients);
  },
};
```
We can play around like the following:
```javascript
const guests1 = restaurant.numGuests ? restaurant.numGuests : 10;
console.log(guests1);

const guests2 = restaurant.numGuests || 10;
console.log(guests2); // 10
```

#

## The AND Operator (`&&`)

```javascript
console.log(0 && 'Charles'); // 0, since it's falsy
console.log(7 && 'Charles'); // Charles, since 7 is truthy so the last value is returned

console.log('Hello' && 23 && null && 'Charles'); // null
```

Let's see another practical example.

Let's suppose our original code is the following:

```javascript
const restaurant = {
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  order: function (starterIndex, mainIndex) {
    return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]];
  },
  orderPasta: function (ing1, ing2, ing3) {
    console.log(`Here is your pasta with ${ing1}, ${ing2}, and ${ing3}.`);
  },
  orderPizza: function (mainIngredient, ...otherIngredients) {
    console.log(mainIngredient);
    console.log(otherIngredients);
  },
};
```
We can play around like the following:
```javascript
// We could do:
if (restaurant.orderPizza) {
  restaurant.orderPizza('mushrooms', 'olive');
}

// But an even simpler way is:
restaurant.orderPizza && restaurant.orderPizza('mushroom', 'olive');
```
