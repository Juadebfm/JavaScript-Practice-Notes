# JavaScript Operators - Beginners Approach

JavaScript operators are symbols that perform operations on values (called operands). Think of them as the mathematical and logical tools that make your code work. Let's explore each type with practical examples you'll use in web development.

## Arithmetic Operators

These perform mathematical calculations, just like a calculator.

```javascript
let price = 100;
let tax = 15;

// Addition (+)
let total = price + tax; // 115 NB: the values on the left and right of the operator i.e price and tax are the operands

// Subtraction (-)
let discount = price - 20; // 80

// Multiplication (*)
let doublePrice = price * 2; // 200

// Division (/)
let halfPrice = price / 2; // 50

// Modulus (%) - returns the remainder
let remainder = 17 % 5; // 2 (17 divided by 5 = 3 remainder 2)

// Exponentiation (**)
let squared = 5 ** 2; // 25

console.log(`Total with tax: $${total}`);
```

**Note:** The modulus operator (%) is super useful for checking if numbers are even/odd or for creating repeating patterns.

```javascript
// Check if a number is even
if (number % 2 === 0) {
  console.log("Even number");
} else {
  console.log("Odd number");
}
```

## Assignment Operators

These assign values to variables and can combine assignment with arithmetic.

```javascript
let score = 0;

// Basic assignment (=)
score = 100;

// Addition assignment (+=)
score += 50; // Same as: score = score + 50 (now 150)

// Subtraction assignment (-=)
score -= 20; // Same as: score = score - 20 (now 130)

// Multiplication assignment (*=)
score *= 2; // Same as: score = score * 2 (now 260)

// Division assignment (/=)
score /= 4; // Same as: score = score / 4 (now 65)

console.log(score); // 65
```

**Web Development Tip:** You'll use `+=` constantly for `building strings` or updating `counters` in your applications.

```javascript
let message = "Hello";
message += " World"; // "Hello World"

let clickCount = 0;
// Every time a button is clicked:
clickCount += 1;
```

## Comparison Operators

These compare values and return true or false - essential for conditional logic.

```javascript
let userAge = 25;
let minimumAge = 18;

// Equal to (==) - compares values, allows type conversion
console.log(5 == "5"); // true (string "5" converts to number 5)

// Strict equal to (===) - compares values AND types
console.log(5 === "5"); // false (number 5 vs string "5")
console.log(5 === 5); // true

// Not equal (!=)
console.log(userAge != 30); // true

// Strict not equal (!==)
console.log(userAge !== "25"); // true (number vs string)

// Greater than (>)
console.log(userAge > minimumAge); // true (25 > 18)

// Less than (<)
console.log(userAge < 30); // true

// Greater than or equal (>=)
console.log(userAge >= 25); // true

// Less than or equal (<=)
console.log(userAge <= 25); // true
```

**Important Note:** Always use `===` and `!==`, i.e _Strict Equality_ in web development to avoid unexpected type conversion bugs.

**Sub-note:** Type conversion can cause weird bugs:

```javascript
console.log(0 == false); // true (0 converts to false)
console.log(0 === false); // false (number vs boolean)
```

## Logical Operators

These work with boolean values (true/false) and are crucial for complex conditions.

These work with boolean values (true/false) and are crucial for complex conditions.

### Truth Tables

**AND Operator (&&)** - Returns true only when BOTH conditions are true:

| A     | B     | A && B |
| ----- | ----- | ------ |
| true  | true  | true   |
| true  | false | false  |
| false | true  | false  |
| false | false | false  |

**OR Operator (||)** - Returns true when AT LEAST ONE condition is true:

| A     | B     | A \|\| B |
| ----- | ----- | -------- |
| true  | true  | true     |
| true  | false | true     |
| false | true  | true     |
| false | false | false    |

**NOT Operator (!)** - Flips the boolean value:

| A     | !A    |
| ----- | ----- |
| true  | false |
| false | true  |

### Code Examples

```javascript
let isLoggedIn = true;
let hasPermission = false;
let userAge = 25;

// AND (&&) - both conditions must be true
if (isLoggedIn && userAge >= 18) {
  console.log("Can access adult content");
}

// OR (||) - at least one condition must be true
if (isLoggedIn || hasPermission) {
  console.log("Can view some content");
}

// NOT (!) - flips true to false, false to true
if (!isLoggedIn) {
  console.log("Please log in");
}

// Combining logical operators
if ((isLoggedIn && userAge >= 18) || hasPermission) {
  console.log("Access granted");
}

// Web Development Pattern: Logical operators are perfect for form validation:

// We create two variables to store an email and password
// These would typically come from a login form that a user filled out

let email = "user@example.com";
let password = "mypassword";

if (email.length > 0 && password.length >= 8) {
  // Valid form submission
  submitForm();
}

/* 

// if (email.length > 0 && password.length >= 8) {

This line checks TWO things at the same time:

email.length > 0 - Is the email field NOT empty?

email.length counts how many characters are in the email (REMEMBER I SAID SOME ARRAY METHODS WORKS ON STRINGS TOO)

"user@example.com" has 16 characters, so 16 > 0 is true

password.length >= 8 - Is the password at least 8 characters long?

"mypassword" has 10 characters, so 10 >= 8 is true

&& - The AND operator means BOTH conditions must be true

Since both are true: true && true = true

*/
```

```javascript
let isLoggedIn = true;
let hasPermission = false;
let userAge = 25;

// AND (&&) - both conditions must be true
if (isLoggedIn && userAge >= 18) {
  console.log("Can access adult content");
}

// OR (||) - at least one condition must be true
if (isLoggedIn || hasPermission) {
  console.log("Can view some content");
}

// NOT (!) - flips true to false, false to true
if (!isLoggedIn) {
  console.log("Please log in");
}

// Combining logical operators
if ((isLoggedIn && userAge >= 18) || hasPermission) {
  console.log("Access granted");
}
```

## Increment and Decrement Operators

Shortcuts for adding or subtracting 1 - you'll see these everywhere in loops and counters.

```javascript
let likes = 10;

// Pre-increment (++variable) - increments first, then returns value
console.log(++likes); // 11 (likes becomes 11, then prints 11)

// Post-increment (variable++) - returns value first, then increments
console.log(likes++); // 11 (prints 11, then likes becomes 12)
console.log(likes); // 12

// Pre-decrement (--variable)
console.log(--likes); // 11 (likes becomes 11, then prints 11)

// Post-decrement (variable--)
console.log(likes--); // 11 (prints 11, then likes becomes 10)
console.log(likes); // 10
```

**Practical Example:** Button click counters in React:

```javascript
let likeCount = 0;

function handleLikeClick() {
  likeCount = likeCount + 1;

  // Update the text on the button to show new count
  document.getElementById("likeButton").textContent = `Likes: ${likeCount}`;
}
```

## String Operators

The main one is concatenation using the `+` operator.

```javascript
let firstName = "John";
let lastName = "Doe";

// String concatenation
let fullName = firstName + " " + lastName; // "John Doe"

// Template literals (modern approach - much easier!)
let greeting = `Hello, ${firstName} ${lastName}!`; // "Hello, John Doe!"
let multiLine = `
    Welcome back, ${firstName}!
    You have ${5} new messages.
`;

console.log(greeting);
```

**Modern Note:** Template literals (backticks) are the preferred way to build strings in modern JavaScript.

## Ternary Operator (Conditional)

A shortcut for simple if-else statements - very popular in React components.

```javascript
let userAge = 20;

// Traditional if-else
let status;
if (userAge >= 18) {
  status = "adult";
} else {
  status = "minor";
}

// Ternary operator (condition ? valueIfTrue : valueIfFalse)
let status2 = userAge >= 18 ? "adult" : "minor";

console.log(status2); // "adult"
```

**React Example:** Perfect for conditional rendering:

```javascript
function showUserProfile(user) {
  let statusText;
  let statusColor;

  if (user.isOnline) {
    statusText = "Online";
    statusColor = "green";
  } else {
    statusText = "Offline";
    statusColor = "gray";
  }

  document.getElementById("userProfile").innerHTML = `
   <h1>${user.name}</h1>
   <span style="color: ${statusColor};">${statusText}</span>
 `;
}

// Example usage:
let user = { name: "John Doe", isOnline: true };
showUserProfile(user);
```

## Type Operators

Useful for checking what type of data you're working with.

```javascript
let name = "Alice";
let age = 30;
let isActive = true;
let user = { name: "Bob" };
let numbers = [1, 2, 3];

// typeof operator
console.log(typeof name); // "string"
console.log(typeof age); // "number"
console.log(typeof isActive); // "boolean"
console.log(typeof user); // "object"
console.log(typeof numbers); // "object" (arrays are objects in JS)

// instanceof operator (for checking specific object types)
console.log(numbers instanceof Array); // true
console.log(user instanceof Array); // false
```

**Debugging Tip:** Use `typeof` when you're not sure what data type a variable contains - super helpful for debugging!

## Common Beginner Mistakes to Avoid

1. **Using `=` instead of `===` for comparison:**

```javascript
// Wrong
if ((userAge = 18)) {
} // This assigns 18 to userAge! 

// Correct
if (userAge === 18) {
} // This compares userAge to 18
```

2. **Confusing `==` and `===`:**

```javascript
console.log("5" == 5); // true (avoid this)
console.log("5" === 5); // false (use this)
```

3. **Not understanding operator precedence:**

```javascript
let result = 5 + 3 * 2; // 11, not 16 (multiplication happens first)
let result2 = (5 + 3) * 2; // 16 (parentheses force addition first)
```

These operators form the foundation of all JavaScript logic. Master these, and you'll be able to build complex web applications with confidence!
