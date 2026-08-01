# 🖥️ Console Debugging

> Learn how to use the JavaScript console effectively to inspect variables, trace program execution, debug API calls, and identify issues in React Native applications.

---

# 📖 Table of Contents

- Introduction
- What is Console Debugging?
- Why Console Debugging?
- How the Console Works
- Setting Up the Console
- console.log()
- console.warn()
- console.error()
- console.table()
- console.group()
- console.groupEnd()
- console.time()
- console.timeEnd()
- console.trace()
- Logging Objects
- Debugging API Responses
- Debugging State
- Debugging Props
- Common Mistakes
- Best Practices
- Practice Exercises
- Summary
- Resources

---

# 📚 Introduction

One of the first debugging techniques every JavaScript developer learns is **Console Debugging**.

Even though React Native provides advanced debugging tools such as **React Native DevTools**, **Breakpoints**, and **Profilers**, the console remains one of the quickest ways to understand what your application is doing.

Imagine you click a button and nothing happens.

Instead of guessing, you can simply log values to the console and inspect what's happening step by step.

---

# 🤔 What is Console Debugging?

Console debugging is the process of printing information to the developer console while your application is running.

Instead of trying to imagine what your code is doing, you can **see the actual values**.

Examples include:

- Variable values
- API responses
- Function calls
- State changes
- Props
- Timers
- Errors
- Warnings

---

# 💡 Why Use Console Debugging?

Console debugging helps answer questions like:

- Did my function execute?
- Is my API returning data?
- What value does this variable have?
- Did my component re-render?
- Is state updating correctly?
- Which function was called first?

Without logging, debugging often becomes guesswork.

---

# 📍 Where Does the Output Appear?

Depending on your setup, console output may appear in:

- Metro Terminal
- React Native DevTools Console
- Chrome DevTools (older workflows)
- Expo CLI logs

---

# 🟢 console.log()

The most commonly used debugging method.

Syntax

```javascript
console.log(value);
```

Example

```javascript
const username = "Aman";

console.log(username);
```

Output

```
Aman
```

---

## Logging Multiple Values

```javascript
const name = "Aman";
const age = 20;

console.log(name, age);
```

Output

```
Aman 20
```

---

## Logging Text

```javascript
console.log("Application Started");
```

Output

```
Application Started
```

---

# 🟡 console.warn()

Used to display warnings.

Example

```javascript
console.warn("Network connection is slow.");
```

Output

```
Warning:
Network connection is slow.
```

Unlike `console.log()`, warnings are highlighted so they're easier to notice.

---

# 🔴 console.error()

Used to display errors.

Example

```javascript
console.error("Unable to fetch user data.");
```

Output

```
Error:
Unable to fetch user data.
```

Use this when something unexpected happens but doesn't necessarily crash the app.

---

# 📊 console.table()

Displays arrays or objects in a table format.

Example

```javascript
const users = [
  { id: 1, name: "Aman" },
  { id: 2, name: "John" },
];

console.table(users);
```

Output

```
┌────┬────┬────────┐
│ id │ name       │
├────┼────┼────────┤
│ 1  │ Aman       │
│ 2  │ John       │
└────┴────┴────────┘
```

Very useful when working with API responses.

---

# 📦 console.group()

Groups related logs together.

```javascript
console.group("Login");

console.log("Checking token");
console.log("Fetching user");
console.log("Navigation");

console.groupEnd();
```

Output

```
▼ Login

Checking token
Fetching user
Navigation
```

---

# ⏱ console.time()

Measure execution time.

```javascript
console.time("Fetch Users");

fetchUsers();

console.timeEnd("Fetch Users");
```

Output

```
Fetch Users: 356ms
```

Useful for finding slow functions.

---

# 🧭 console.trace()

Shows the current call stack.

```javascript
function first() {
    second();
}

function second() {
    console.trace();
}

first();
```

Output

```
second()

first()

App()
```

Useful when you're unsure where a function is being called from.

---

# 📦 Logging Objects

Instead of

```javascript
console.log(user.name);
```

Log the entire object.

```javascript
console.log(user);
```

This helps identify missing properties.

---

# 🌐 Debugging API Responses

Example

```javascript
const response = await fetch(API_URL);

const data = await response.json();

console.log(data);
```

Before using the response, inspect it.

Never assume the API returns what you expect.

---

# ⚛️ Debugging React State

Example

```javascript
const [count, setCount] = useState(0);

console.log(count);
```

Click the button.

Observe how the value changes after every render.

---

# 📦 Debugging Props

```javascript
function Profile(props) {

    console.log(props);

    return (
        ...
    );

}
```

Inspect every prop received by the component.

---

# 🚫 Common Mistakes

❌ Leaving hundreds of console.logs in production.

❌ Logging sensitive information like passwords or tokens.

❌ Logging inside loops unnecessarily.

❌ Ignoring warning messages.

❌ Assuming API responses are always correct.

---

# 💡 Best Practices

✅ Remove unnecessary logs before release.

✅ Log meaningful messages.

Instead of

```javascript
console.log(data);
```

Use

```javascript
console.log("User Data:", data);
```

This makes logs much easier to understand.

---

# 🎯 Practice Exercise

1. Print a variable using `console.log()`.
2. Display a warning with `console.warn()`.
3. Display an error with `console.error()`.
4. Log an array using `console.table()`.
5. Measure execution time using `console.time()`.
6. Use `console.trace()` inside a nested function.

---

# 📝 Summary

After completing this chapter, you should understand:

- console.log()
- console.warn()
- console.error()
- console.table()
- console.group()
- console.time()
- console.trace()
- Logging API responses
- Logging React state
- Logging props
- Best practices for console debugging

---

# 📚 Official Resources

- React Native Documentation
- Expo Documentation
- MDN Console API

---

## 🚀 Next Chapter

➡️ **04-Breakpoints.md**

You'll learn how to pause your application, inspect variables in real time, step through your code line by line, and debug without relying on `console.log()`.