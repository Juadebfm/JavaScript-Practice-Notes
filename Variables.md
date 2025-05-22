# Understanding Variables: A Beginner's Guide

## Table of Contents

- [What are Variables?](#what-are-variables)
- [Declaring Variables](#declaring-variables)
- [Variable Types](#variable-types)
- [Naming Conventions](#naming-conventions)
- [Scope of Variables](#scope-of-variables)
- [Best Practices](#best-practices)

## What are Variables?

Variables are containers that store data values. Think of them as labeled boxes or even labeled doors in a building, where you can put different types of information that your program needs to remember.

```js
let username = "Juadeb"; // This variable stores the string "Juadeb"
```

## Declaring Variables

In JavaScript, you can declare variables in three ways:

```js
// Using let (recommended for values that will change)
let age = 25;

// Using const (for values that won't change)
const PI = 3.14159;

// Using var (older way, generally avoided in modern code)
var score = 100;
```

## Variable Types

JavaScript has several basic data types:

```js
let name = "John"; // String
let age = 30; // Number
let isLoggedIn = true; // Boolean (true/false)
let userSettings = null; // Null (intentionally empty)
let futureData; // Undefined (not assigned yet)
let userProfile = {
  // Object
  name: "John",
  age: 30,
};
let hobbies = ["reading", "coding", "music"]; // Array
```

## Naming Conventions

Good variable names are descriptive and follow these rules:

```js
// Camel case (recommended)
let firstName = "John";

// Use meaningful names
let userAgeInYears = 25; // Good
let x = 25; // Bad: not descriptive

// Cannot start with a number
// let 1user = "John";      // Error!

// Can include letters, numbers, $ and _
let user_score = 100; // Valid but not common in JS
let $specialValue = 42; // Valid
```

## Scope of Variables

Variables have different visibility depending on where they're declared:

```js
// Global scope (available everywhere)
const siteName = "Juadeb Code Learner";

function updateProfile() {
  // Function scope (only available inside this function)
  let userId = 12345;

  if (userId > 0) {
    // Block scope (only available in this if block)
    let message = "Profile updated";
    console.log(message);
  }

  // console.log(message);  // Error: message not available here
}
```

## Best Practices

- Use `const` by default, and `let` when you know the value will change
- Give variables meaningful, descriptive names
- Keep variable names concise but clear
- Use camelCase for multi-word variable names
- Declare variables at the top of their scope when possible
- Avoid global variables when you can

Remember: variables are the building blocks of your program - they store the information that makes your application work!
