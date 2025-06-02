# Javascript: FetchAPI And All You Need To Know

## Table of Contents

1. [What is the Fetch API?](#what-is-the-fetch-api)
2. [Understanding HTTP and HTTPS](#understanding-http-and-https)
3. [Fetch API Basics](#fetch-api-basics)
4. [Request Objects Deep Dive](#request-objects-deep-dive)
5. [Response Objects Explained](#response-objects-explained)
6. [Practical Examples](#practical-examples)
7. [Error Handling](#error-handling)
8. [Best Practices](#best-practices)
9. [Common Patterns](#common-patterns)
10. [Exercises](#exercises)

---

## What is the Fetch API?

The Fetch API is a modern JavaScript interface that allows you to make HTTP requests to servers. Think of it as a way for your web page to "talk" to other servers on the internet to get or send data. In class we imagined it as the driver and the car that goes to and from the backend to the frontend carrying either `requests` or `responses`.

### Why Use Fetch API?

- **Modern**: Replaces older XMLHttpRequest (Which was the system we use before now)
- **Promise-based**: Works with `.then()` and `.catch()`
- **Flexible**: Can handle various data types
- **Built-in**: No external libraries needed

### Real-world Analogy

Imagine you're at a restaurant:

- You (JavaScript) want to order food
- The waiter (Fetch API) takes your order to the kitchen
- The kitchen (Server/API) prepares your food
- The waiter brings back your food (Response)

Or Imagine:

- You (Frontend) want to send something somewhere, you go to the park
- Have some discussion (frontend request) with the driver (fetchAPI)
- The backend (the receiver) gets this thing you wanted to send and then it sends a response to affirm receipt or not

---

## Understanding HTTP and HTTPS

### What is HTTP?

**HTTP** (HyperText Transfer Protocol) is the foundation of data communication on the web. It's a set of rules that determines how messages are formatted and transmitted.

### What is HTTPS?

**HTTPS** (HTTP Secure) is HTTP with encryption. It's like sending a letter in a locked box instead of a postcard.

### Key Differences:

| HTTP              | HTTPS                      |
| ----------------- | -------------------------- |
| Not encrypted     | Encrypted with SSL/TLS     |
| Port 80           | Port 443                   |
| Fast but insecure | Slightly slower but secure |
| `http://`         | `https://`                 |

### HTTP Methods (Actions)

- **GET**: Retrieve data (like reading a book)
- **POST**: Send new data (like submitting a form)
- **PUT**: Update entire resource (like rewriting a page or changing user information)
- **PATCH**: Update part of resource (like editing a paragraph)
- **DELETE**: Remove data (like throwing away a paper)

---

## Fetch API Basics

### Basic Syntax

```javascript
fetch(url)
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error("Error:", error));
```

### Simple GET Request Example

```javascript
// Let's get information about one user
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then(response => response.json())
  .then(user => {
    console.log("User name:", user.name);
    console.log("User email:", user.email);
  })
  .catch(error => {
    console.log("Something went wrong:", error);
  });
```

### What happens step by step:

1. `fetch()` sends a request to get user data
2. `.then()` waits for the response and converts it to JSON
3. `.then()` receives the actual user data and displays it
4. `.catch()` handles any errors that might happen

---

## Request Objects Deep Dive

### What is a Request Object?

A Request object represents an HTTP request. When you use `fetch()`, you can either pass a URL string or a Request object.

### Creating Request Objects

```javascript
// Method 1: Simple URL string (what we've been doing)
fetch("https://api.example.com/data");

// Method 2: Using a Request object
const request = new Request("https://api.example.com/data", {
  method: "GET",
  headers: {
    "Content-Type": "application/json"
  }
});
fetch(request);
```

### Request with Options (The Complete Version)

```javascript
fetch("https://api.example.com/users", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "Authorization": "Bearer your-token-here"
  },
  body: JSON.stringify({
    name: "John Doe",
    email: "john@example.com"
  })
})
.then(response => response.json())
.then(data => console.log("Success:", data))
.catch(error => console.log("Error:", error));
```

### Request Options Explained

#### Headers
Headers provide additional information about the request:

```javascript
const headers = {
  "Content-Type": "application/json",      // What type of data we're sending
  "Authorization": "Bearer token123",      // Login credentials
  "Accept": "application/json"             // What type of data we want back
};
```

#### Body
The data you're sending (only for POST, PUT, PATCH):

```javascript
// Sending JSON data
body: JSON.stringify({ name: "John", age: 30 })

// Sending form data (like a file upload)
const formData = new FormData();
formData.append("name", "John");
body: formData

// Sending plain text
body: "Hello, server!"
```

---

## Response Objects Explained

### What is a Response Object?

A Response object represents the server's response to your request. It contains the data, status codes, headers, and methods to process the response.

### Response Properties

```javascript
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then(response => {
    console.log("Status:", response.status);        // 200, 404, 500, etc.
    console.log("Status Text:", response.statusText); // 'OK', 'Not Found', etc.
    console.log("Is it OK?", response.ok);          // true if status 200-299
    console.log("URL:", response.url);              // The URL we fetched from
    
    return response.json(); // Convert response to JSON
  })
  .then(data => {
    console.log("User data:", data);
  });
```

### Response Methods (Different ways to read data)

```javascript
fetch("https://api.example.com/data")
  .then(response => {
    // Choose ONE of these based on what type of data you expect:
    
    return response.json();        // For JSON data (most common)
    // return response.text();     // For plain text
    // return response.blob();     // For files/images
  })
  .then(data => {
    console.log("Data:", data);
  });
```

### Status Codes Explained

```javascript
fetch("https://api.example.com/data")
  .then(response => {
    if (response.status >= 200 && response.status < 300) {
      console.log("Success!");
      return response.json();
    } else if (response.status === 404) {
      console.log("Data not found or frontend issues");
    } else if (response.status >= 500) {
      console.log("Server error");
    } else {
      console.log("Something went wrong");
    }
  })
  .then(data => {
    if (data) {
      console.log("Data:", data);
    }
  });
```

Common status codes:
- **200**: OK - Success
- **201**: Created - Resource created successfully  
- **400**: Bad Request - Invalid request (from the frontend)
- **401**: Unauthorized - Authentication required
- **403**: Forbidden - Access denied
- **404**: Not Found - Resource doesn't exist
- **500**: Internal Server Error - Server problem

---

## Practical Examples

### Example 1: Get and Display One User

```javascript
function showUser() {
  fetch("https://jsonplaceholder.typicode.com/users/1")
    .then(response => response.json())
    .then(user => {
      document.getElementById("user-info").innerHTML = `
        <h2>${user.name}</h2>
        <p>Email: ${user.email}</p>
        <p>Phone: ${user.phone}</p>
      `;
    })
    .catch(error => {
      document.getElementById("user-info").innerHTML = "Failed to load user";
      console.log("Error:", error);
    });
}

// Call the function
showUser();
```

### Example 2: Get and Display All Users

```javascript
function showAllUsers() {
  fetch("https://jsonplaceholder.typicode.com/users")
    .then(response => response.json())
    .then(users => {
      let userHTML = "";
      
      users.forEach(user => {
        userHTML += `
          <div>
            <h3>${user.name}</h3>
            <p>${user.email}</p>
          </div>
        `;
      });
      
      document.getElementById("user-list").innerHTML = userHTML;
    })
    .catch(error => {
      document.getElementById("user-list").innerHTML = "Failed to load users";
      console.log("Error:", error);
    });
}

showAllUsers();
```

### Example 3: Create a New Post

```javascript
function createPost() {
  const newPost = {
    title: "My New Post",
    body: "This is what I want to say",
    userId: 1
  };

  fetch("https://jsonplaceholder.typicode.com/posts", {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify(newPost)
  })
  .then(response => response.json())
  .then(data => {
    console.log("Post created:", data);
    alert("Post created successfully!");
  })
  .catch(error => {
    console.log("Error:", error);
    alert("Failed to create post");
  });
}

createPost();
```

### Example 4: Update User Information

```javascript
function updateUser() {
  const updatedInfo = {
    name: "John Smith",
    email: "johnsmith@example.com",
    phone: "555-123-4567"
  };

  fetch("https://jsonplaceholder.typicode.com/users/1", {
    method: "PUT",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify(updatedInfo)
  })
  .then(response => response.json())
  .then(data => {
    console.log("User updated:", data);
    alert("User updated successfully!");
  })
  .catch(error => {
    console.log("Error:", error);
    alert("Failed to update user");
  });
}

updateUser();
```

---

## Error Handling

### Basic Error Handling

```javascript
fetch("https://api.example.com/data")
  .then(response => {
    if (!response.ok) {
      throw new Error("Something went wrong");
    }
    return response.json();
  })
  .then(data => {
    console.log("Success:", data);
  })
  .catch(error => {
    console.log("Error happened:", error);
    // Show user-friendly message
    alert("Sorry, something went wrong. Please try again.");
  });
```

### Checking Different Types of Errors

```javascript
fetch("https://api.example.com/data")
  .then(response => {
    if (response.status === 404) {
      throw new Error("Data not found");
    }
    if (response.status === 500) {
      throw new Error("Server error");
    }
    if (!response.ok) {
      throw new Error("Request failed");
    }
    return response.json();
  })
  .then(data => {
    console.log("Data:", data);
  })
  .catch(error => {
    if (error.message === "Data not found") {
      alert("The information you're looking for doesn't exist");
    } else if (error.message === "Server error") {
      alert("The server is having problems. Try again later");
    } else {
      alert("Something went wrong. Please try again");
    }
  });
```

---

## Best Practices

### 1. Always Handle Errors

```javascript
// ❌ Bad - no error handling
fetch("/api/data")
  .then(response => response.json())
  .then(data => console.log(data));

// ✅ Good - with error handling
fetch("/api/data")
  .then(response => {
    if (!response.ok) {
      throw new Error("Request failed");
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => {
    console.log("Error:", error);
    alert("Something went wrong");
  });
```

### 2. Always Check if Response is OK

```javascript
// ✅ Always check response status
fetch("/api/data")
  .then(response => {
    if (!response.ok) {
      throw new Error(`Error: ${response.status}`);
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.log(error));
```

### 3. Set Correct Headers for JSON

```javascript
// ✅ When sending JSON data, set the content type
fetch("/api/data", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({name: "John", age: 25})
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.log(error));
```

---

## Common Patterns

### 1. Show Loading Message

```javascript
function loadUserData() {
  // Show loading message
  document.getElementById("content").innerHTML = "Loading...";
  
  fetch("/api/users")
    .then(response => {
      if (!response.ok) {
        throw new Error("Failed to load");
      }
      return response.json();
    })
    .then(users => {
      // Show the data
      let userHTML = "";
      users.forEach(user => {
        userHTML += `<div>${user.name}</div>`;
      });
      document.getElementById("content").innerHTML = userHTML;
    })
    .catch(error => {
      // Show error message
      document.getElementById("content").innerHTML = "Failed to load users";
    });
}
```

### 2. Form Submission

```javascript
function submitForm() {
  // Get form data
  const name = document.getElementById("name").value;
  const email = document.getElementById("email").value;
  
  // Send to server
  fetch("/api/users", {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      name: name,
      email: email
    })
  })
  .then(response => {
    if (!response.ok) {
      throw new Error("Failed to submit");
    }
    return response.json();
  })
  .then(data => {
    alert("Form submitted successfully!");
    // Clear the form
    document.getElementById("name").value = "";
    document.getElementById("email").value = "";
  })
  .catch(error => {
    alert("Failed to submit form. Please try again.");
  });
}
```

### 3. Delete Item

```javascript
function deleteUser(userId) {
  if (confirm("Are you sure you want to delete this user?")) {
    fetch(`https://jsonplaceholder.typicode.com/users/${userId}`, {
      method: "DELETE"
    })
    .then(response => {
      if (!response.ok) {
        throw new Error("Failed to delete");
      }
      alert("User deleted successfully!");
      // Remove from page
      document.getElementById(`user-${userId}`).remove();
    })
    .catch(error => {
      alert("Failed to delete user");
    });
  }
}
```

---

## Exercises

### Exercise 1: Basic User Profile Display

Create a simple webpage that shows user information.

**Requirements:**
- Fetch user data from `https://jsonplaceholder.typicode.com/users/1`
- Display the user's name, email, and phone number
- Show "Loading..." while fetching
- Show error message if something goes wrong

**HTML Starter:**
```html
<div id="user-profile">
  <div id="loading">Loading...</div>
  <div id="user-data"></div>
  <div id="error" style="display: none;"></div>
</div>
<button onclick="loadUser()">Load User</button>
```

**Your Task:** Write the `loadUser()` function.

### Exercise 2: Simple Post Creator

Build a form that creates a new post.

**Requirements:**
- Create a form with title and content fields
- Send the data to `https://jsonplaceholder.typicode.com/posts`
- Show success or error messages
- Clear the form after successful submission

### Exercise 3: User List with Delete

Create a user list where you can delete users.

**Requirements:**
- Load all users from `https://jsonplaceholder.typicode.com/users`
- Display each user with a delete button
- When delete is clicked, remove the user from the list
- Show confirmation before deleting

### Exercise 4: Simple Search

Build a search feature for posts.

**Requirements:**
- Load posts from `https://jsonplaceholder.typicode.com/posts`
- Add a search box that filters posts by title
- Update the display as the user types
- Handle the case when no posts match

---

## Summary

The Fetch API is a powerful tool for making HTTP requests in JavaScript. Remember these key points:

1. **Always handle errors** - Use `.catch()` to handle problems
2. **Check response status** - Use `response.ok` or check `response.status`
3. **Use the right headers** - Set `Content-Type` when sending JSON
4. **Give user feedback** - Show loading, success, and error messages
5. **Start simple** - Begin with GET requests, then move to POST, PUT, DELETE

Practice with simple examples first, then gradually work on more complex features. The most important thing is to always handle errors and give users clear feedback about what's happening!