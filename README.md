# JavaScript Logical Operators

## Overview
In this lesson, we'll learn how to negate and combine expressions with JavaScript's three logical operators: NOT (`!`), AND (`&&`), and OR (`||`).

![Logical.](https://user-images.githubusercontent.com/17556281/28996880-439ba4ca-79d6-11e7-9500-3cb4a3ab8b72.gif)

## Objectives
1. Invert the truthiness of an expression with the `!` operator.
2. Convert an expression into its boolean equivalent with a double bang (`!!`).
3. Combine conditions with the `&&` and `||` operators.

## NOT
The logical NOT operator (`!`), also called the _bang operator_, operates on a single expression, returning the inverse of the expression's truthiness. If `x` resolves to a truthy value, `!x` evaluates to `false`. If `x` is falsy, `!x` evaluates to `true`:
```js
const truthyValue = "This value is truthy.";
//=> undefined

!truthyValue;
//=> false

const falsyValue = 0;
//=> undefined

!falsyValue;
//=> true
```

### Boolean shortcut
In the lesson on conditional statements, we passed values into the `Boolean()` object to check their truthiness. As a shorter way to convert any value into a boolean, we can use two bang operators:
```js
const truthyValue = "This value is truthy.";
//=> undefined

!truthyValue;
//=> false

!!truthyValue;
//=> true
```

Reading from left-to-right, the JavaScript engine sees the first `!` and looks to the right to check what we're asking it to invert (`!truthyValue`). It then sees the second `!` and looks to the right _again_, this time finding our `truthyValue` variable. The engine resolves `truthyValue` to `"This value is truthy."` and then executes the second `!` operator on it. `!truthyValue` evaluates to `false`, so instead of `!!truthyValue` we're now looking at `!false`. The remaining `!` operator then executes on `false`, inverting the falsy value and evaluating to `true`.

Try inverting various values in the browser's JS console to get a feel for the bang operator. See what happens when you stack a ton of them: `!!!!!!!!!truthyValue`.

Onto the next!

![Not!](https://user-images.githubusercontent.com/17556281/28983250-ea2d74e0-7926-11e7-8fed-8a6029d9903c.gif)

## AND
The logical AND (`&&`) operator takes two expressions:
```js
expression1 && expression2
```

First, the `&&` operator checks the first expression. If the expression evaluates to a falsy value, `&&` returns that value and exits _without ever checking the second expression_:
```js
false && 'Anything'
//=> false

// 4 % 2 evaluates to 0, which is falsy
4 % 2 && 'Anything'
//=> 0
```

If the first expression evaluates to a truthy value, `&&` then returns whatever the second expression evaluates to:
```js
true && false
//=> false

1 + 1 && 'Whatever'
//=> "Whatever"

'The truthiest of truthy strings' && 9 ** 2
//=> 81
```

## OR
The logical OR (`||`) operator also takes two expressions:
```js
expression1 || expression2
```

If the first expression evaluates to a truthy value, that value is immediately returned and the second expression is never evaluated:
```js
true || 'Whatever'
//=> true

1 + 1 || 'Whatever'
//=> 2
```

If the first expression evaluates to a falsy value, `||` returns whatever the second expression evaluates to:
```js
false || 'Whatever'
//=> "Whatever"

1 === 2 || 2 ** 8
//=> 256

'' || 'Not ' + 'an ' + 'empty ' + 'string'
//=> "Not an empty string"
```

## Linking conditions
The `&&` and `||` operators are often used to link multiple conditions in a conditional statement:
```js
let user = 'Charles Babbage';
//=> undefined

let friendCount = 3;
//=> undefined

let message, messageColor;
//=> undefined

if (user && friendCount) {
  message = `Hi ${user}! You have ${friendCount} ${friendCount === 1 ? 'friend' : 'friends'}!`;
} else {
  if (user) {
    message = 'Please sign in.';
  } else {
    message = 'Link up with your friends to get the most out of Flatbook!';
  }
}
//=> "Hi Charles Babbage! You have 3 friends!"

if (message === 'Please sign in.' || message === 'Link up with your friends to get the most out of Flatbook!') {
  messageColor = 'red';
} else if (friendCount >= 1 && friendCount <= 10) {
  messageColor = 'blue';
} else if (friendCount >= 11 && friendCount <= 50) {
  messageColor = 'purple';
} else {
  messageColor = 'rainbow';
}
//=> "blue"
```

![That's logic!](https://user-images.githubusercontent.com/17556281/28996875-12d91142-79d6-11e7-8dfe-c0c7bd9f1ffa.gif)

## Resources
- MDN
  + [Logical operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)
  + [Review of conditionals, comparisons, and logical operators](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals)
