# JavaScript Conditionals - Making Decisions in JavaScript

Imagine you're writing instructions for a robot, or a machine or even sending a child errand and you want them to check if it's raining, if it rains you want them to stay back, if it's not raining you want them to go do the errand. Sometimes you want the robot/machine/child to do different things based on what's happening around it/him/her. That's exactly what conditional statements do in JavaScript - they help your code make decisions!:

## Why Do We Need Conditional Statements?

Normally, JavaScript reads your code from top to bottom, line by line, like reading a book. But sometimes you want to say:

- "If it's raining, grab an umbrella"
- "If the user is logged in, show their profile"
- "If the password is wrong, show an error message"

This is where conditional statements come in handy!

## Two Main Ways Code Can Change Direction:

1. Making Choices (Conditional execution)

"Do this ONLY IF something is true"
Like: "IF the user clicked the button, THEN change the color"

2. Repeating Actions (Repetitive execution)

"Keep doing this WHILE something is true"
Like: "WHILE there are items in the shopping cart, keep calculating the total"

Note: We'll focus on making choices today. Repetitive execution (loops) is a topic for another day!

## The 5 Ways to Make Decisions in JavaScript:

1. if - "Do this IF something is true"
2. if else - "Do this IF true, otherwise do that"
3. if else if else - "Check multiple conditions in order"
4. switch - "Pick one option from many choices"
5. ternary operator - "Quick shortcut for simple if-else decisions"

Each tool is perfect for different situations, just like how you'd use different tools to fix different things around the house!

Remember: You'll use those comparison operators (===, >, <) and logical operators (&&, ||, !) we learned earlier to create the conditions that help your code make these decisions.

### 1. The if Statement - Basic Decision Making

This is like asking "Is this true?" If yes, do something. If no, skip it and move on.

```javascript
// Real-world example: "If it's raining, take an umbrella"

let isRaining = true;

if (isRaining) {
  console.log("Take an umbrella!");
}

console.log("Leave the house"); // This always runs
```

```javascript
// Web development example:

let userAge = 17;

if (userAge >= 18) {
  console.log("Show age-restricted content");
}

// If user is under 18, nothing happens - the code just continues
```

Syntax breakdown:

- if - the keyword that starts the decision
- (condition) - the question you're asking (must be true or false)
- { } - the code that runs if the condition is true

### 2. The if else Statement - Either This OR That

This is like having a backup plan. "If this is true, do A. Otherwise, do B."

```javascript
let isSunny = false;

if (isSunny) {
  console.log("Go to the beach!");
} else {
  console.log("Stay home and read a book");
}
```

```javascript
// Web development example:

let isLoggedIn = false;

if (isLoggedIn) {
  console.log("Welcome back! Here's your dashboard");
} else {
  console.log("Please log in to continue");
}
```

Key point: With if else, one of the two blocks will ALWAYS run. There's no middle ground!

### 3. The if else if else Statement - Multiple Choices

This is like having a series of questions with different outcomes. Perfect when you have more than two possibilities.

```javascript
// Real-world example: Choosing what to wear based on temperature

let temperature = 75;

if (temperature > 80) {
  console.log("Wear shorts and a t-shirt");
} else if (temperature > 60) {
  console.log("Wear jeans and a light jacket");
} else if (temperature > 40) {
  console.log("Wear warm clothes and a coat");
} else {
  console.log("Wear heavy winter gear!");
}
```

```javascript
// Web development example: User role permissions

let userRole = "admin";

if (userRole === "admin") {
  console.log("Access to everything!");
} else if (userRole === "moderator") {
  console.log("Access to user management");
} else if (userRole === "user") {
  console.log("Access to basic features");
} else {
  console.log("Please contact support for access");
}
```

How it works:

1. JavaScript checks each condition from top to bottom
2. As soon as one condition is true, it runs that code and skips the rest
3. If none are true, the final else runs (if you have one)

### 4. The switch Statement - Menu of Options

When you have many `specific values` to check, switch is cleaner than multiple if else if statements. Think of it like a restaurant menu - you pick one exact option.

```javascript
// Real-world example: Days of the week

let day = "Monday";

switch (day) {
  case "Monday":
    console.log("Start of the work week!");
    break;
  case "Tuesday":
    console.log("Tuesday blues");
    break;
  case "Wednesday":
    console.log("Hump day!");
    break;
  case "Saturday":
  case "Sunday":
    console.log("Weekend time!");
    break;
  default:
    console.log("Invalid day");
}
```

```javascript
// Web development example: Button actions

let buttonPressed = "save";

switch (buttonPressed) {
  case "save":
    console.log("Saving your work...");
    break;
  case "delete":
    console.log("Are you sure you want to delete?");
    break;
  case "cancel":
    console.log("Operation cancelled");
    break;
  default:
    console.log("Unknown action");
}
```

Important notes:

1. break stops the switch from continuing to the next case
2. default is like the final else - runs if no cases match
3. You can group cases together (like Saturday and Sunday above)

### 5. The Ternary Operator - Quick Decisions

This is the speed version of if else. Perfect for simple decisions that fit on one line.

-_Format: condition ? valueIfTrue : valueIfFalse_\_

```javascript
// Real-world example:

let age = 20;
let message = age >= 18 ? "You can vote!" : "Too young to vote";
console.log(message);
```

```javascript
// Setting CSS classes
let isActive = true;
let buttonClass = isActive ? "btn-active" : "btn-inactive";

// Displaying different text
let itemCount = 5;
let text = itemCount === 1 ? "1 item" : `${itemCount} items`;

// Quick validation
let email = "user@example.com";
let isValid = email.includes("@") ? "Valid email" : "Invalid email";
```

When to use:

- ✅ Simple true/false decisions
- ✅ Assigning values based on conditions
- ✅ When you want concise code
- ❌ Complex logic (use regular if-else instead)

## Choosing the Right Tool

- Use if when:

  - You only need to do something if a condition is true
  - Example: "If user is admin, show admin panel"

- Use if else when:

  - You have exactly two options
  - Example: "If logged in, show dashboard, else show login page"

- Use if else if else when:

  - You have multiple conditions to check in order
  - Example: "If A, then X. If B, then Y. If C, then Z. Otherwise, do default."

- Use switch when:

  - You're checking one variable against many specific values
  - Example: "If day is Monday do X, if Tuesday do Y, if Wednesday do Z..."

- Use ternary operator when:

  - You need a quick, simple decision on one line
  - Example: "Show 'Online' if user is active, else show 'Offline'"

Practice Makes Perfect!
The best way to learn conditionals is to practice with real scenarios. Try building:

A simple calculator that does different operations based on user input
A weather app that shows different messages based on temperature
A login system that shows different content based on user status

Remember: Every app you use makes thousands of these decisions behind the scenes!
