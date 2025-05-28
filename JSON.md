# JavaScript JSON - Storing and Sharing Information In JavaScript

Think of JSON like a universal language for computers to share information with each other. Just like how people from different countries might use English as a common language to communicate, computers use JSON to "talk" to each other.

## What is JSON?

`JSON` stands for `JavaScript Object Notation`, but don't let the name confuse you - it's not just for JavaScript! Even though it started there, now almost every programming language can understand `JSON`.

## Why do we need JSON?

Imagine you have a friend in another city, and you want to send them your favorite recipe. You can't send the actual cake through the mail, so you write down the recipe on paper. JSON works the same way for computers - it's like writing down information in a format that any computer can read and understand.

## What does JSON look like?

JSON looks very similar to how we write objects and or arrays in JavaScript, but it's always saved as text (like a text message).

**Here's a simple example:**

```json
{
  "name": "John",
  "age": 25,
  "city": "New York"
}
```

This is like having a digital business card that any computer can read!

## When do we use JSON?

The most common use is when websites (frontend or client) need to get information from servers(backend). For example, when you check the weather on your phone, your app sends a request to a weather server, and the server sends back the weather information in `JSON` format.
`JSON` is popular because it's _lightweight_ (doesn't take up much space) and easy for both humans and computers to read and write.

```json
{
  "users": [
    {
      "firstName": "Julius",
      "lastName": "Adebowale",
      "age": 250,
      "email": "juadebgabriel@gmail.com"
    },
    {
      "firstName": "femi",
      "lastName": "gabriel",
      "age": 25,
      "email": "femi@gabriel.com"
    },
    {
      "firstName": "doyin",
      "lastName": "gabriel",
      "age": 28,
      "email": "doyin@gabriel.com"
    }
  ]
}
```

**Breaking it down piece by piece:**

Think of this like a filing cabinet:

- The big {} curly brackets are like the filing cabinet itself
- Inside, we have a folder labeled "users"
- This folder contains a list [] (arrays) of user cards
- Each user card {} has information like name, age, and email

## The Key Difference between JSON & Objects: Quotation Marks

Here's the most important thing to remember - JSON is very picky about quotation marks!
In JavaScript objects (what we normally write):

```js
{
  firstName: "Julius",    // No quotes around the key
  age: 25
}
```

```json
{
  "firstName": "Julius", // Quotes around EVERYTHING!
  "age": 25
}
```

**Why the difference?**

Think of JSON like sending a formal letter - it has strict rules about format. JavaScript objects are like talking to a friend - more relaxed rules. When computers from different systems need to share data, they use the "formal letter" format (JSON) so there's no confusion.
The good news: JavaScript can easily convert back and forth between these two formats, so you don't have to worry about rewriting everything by hand!

## Converting JSON to JavaScript Object

When you're working with websites and apps, you'll often receive information in JSON format (remember, that's the "formal letter" format). But to actually use that information in your JavaScript code, you need to convert it into a regular JavaScript object first.
Think of it like translation:

JSON = A formal document written in "computer language"
JavaScript Object = The same information, but in a format your JavaScript code can easily work with

### The Two Magic Methods

JavaScript gives us two built-in tools to convert back and forth:

#### 1. JSON.parse() - Converting JSON to Object

This takes JSON text and turns it into a JavaScript object you can use.

```js
// JSON as text (what you might receive from a server)
let jsonText = '{"name": "Juadeb", "age": 35, "city": "Lagos"}';

// Convert JSON text to JavaScript object
let person = JSON.parse(jsonText);

// Now you can use it like a normal object!
console.log(person.name); // Shows: Juadeb
console.log(person.age); // Shows: 35
```

#### 2. JSON.stringify() - Converting Object to JSON

This takes a JavaScript object and turns it into JSON text (useful when sending data to a server).

```js
// Regular JavaScript object
let student = {
  name: "David",
  grade: "A",
  subjects: ["Math", "English"],
};

// Convert object to JSON text
let jsonText = JSON.stringify(student);
console.log(jsonText);
// Shows: '{"name":"David","grade":"A","subjects":["Math","English"]}'
```

**Easy way to remember:**

`parse()` = "Please turn this JSON text into something I can use!"
`stringify()` = "Please turn this object into JSON text I can send!"

_Real-world example:_

When you check your social media feed, your app receives user posts as JSON, uses JSON.parse() to convert them into objects, and then displays the information on your screen.
