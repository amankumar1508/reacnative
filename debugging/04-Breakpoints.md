# 🛑 Breakpoints

> Learn how to pause your React Native application, inspect variables, follow code execution, and identify bugs using breakpoints.

---

# 📖 Table of Contents

- Introduction
- What is a Breakpoint?
- Why Use Breakpoints?
- How Breakpoints Work
- When Should You Use Breakpoints?
- Setting Up Breakpoints
- Types of Breakpoints
- Debug Controls
- Inspecting Variables
- Watching Expressions
- Debugging Async Code
- Conditional Breakpoints
- Breakpoints vs console.log()
- Real-World Examples
- Common Mistakes
- Best Practices
- Practice Exercises
- Summary
- Resources

---

# 📚 Introduction

Imagine your application crashes when a user presses a button.

Your first instinct might be to write:

```javascript
console.log(user);
console.log(token);
console.log(response);
console.log(data);
```

Soon your code becomes full of logging statements.

Instead, professional developers use **Breakpoints**.

A breakpoint lets you pause your application at a specific line of code and inspect everything happening at that exact moment.

You don't have to guess.

You don't have to add dozens of `console.log()` statements.

You simply pause execution and inspect your application's current state.

---

# 🤔 What is a Breakpoint?

A breakpoint is a marker placed on a line of code.

When JavaScript reaches that line, execution stops temporarily.

While paused, you can inspect:

- Variables
- Objects
- Arrays
- State
- Props
- Function arguments
- Call Stack
- Memory values

Nothing executes until you decide to continue.

Think of it like pressing the **Pause** button on a video.

---

# 🎯 Why Use Breakpoints?

Breakpoints help answer questions like:

- Why is this variable undefined?
- Why didn't this function execute?
- Is this condition true?
- What data came from the API?
- Why didn't state update?
- Which function was called first?

Instead of printing values, you inspect them directly.

---

# ⚙️ How Breakpoints Work

Suppose your code is:

```javascript
function login(user) {
  const token = generateToken(user);

  console.log(token);

  navigate("Home");
}
```

If you place a breakpoint on:

```javascript
const token = generateToken(user);
```

Execution stops **before** the next line runs.

At this point you can inspect:

- user
- token (after stepping over)
- current function
- call stack

---

# 📍 Where Can You Add Breakpoints?

You can add breakpoints almost anywhere:

✅ Inside Components

```javascript
function Profile() {

}
```

---

✅ Inside Event Handlers

```javascript
const handleLogin = () => {

};
```

---

✅ Inside API Calls

```javascript
async function fetchUsers() {

}
```

---

✅ Inside useEffect()

```javascript
useEffect(() => {

}, []);
```

---

✅ Inside Custom Hooks

```javascript
function useAuth() {

}
```

---

# 🚀 Setting Up Breakpoints

Using React Native DevTools:

1. Open React Native DevTools.
2. Open the **Sources** tab.
3. Open your project files.
4. Click the line number.
5. A blue/red marker appears.
6. Reload or trigger the code.
7. Execution pauses automatically.

---

# 📷 Screenshot

```
images/breakpoint.png
```

---

# ▶ Debug Controls

When execution pauses, you'll see several controls.

---

## Continue ▶

Resumes execution until the next breakpoint.

---

## Step Over ⤵

Executes the current line.

Does **not** enter functions.

Example

```javascript
login();
```

It simply runs the function.

---

## Step Into ⬇

Moves inside the function.

Example

```javascript
login();
```

Instead of executing immediately, it opens:

```javascript
function login() {

}
```

Useful when debugging function internals.

---

## Step Out ⬆

Suppose you're inside:

```javascript
function login() {

}
```

Step Out finishes this function and returns to the caller.

---

## Restart ↺

Restarts the current debugging session.

---

# 🔍 Inspecting Variables

Suppose execution pauses here:

```javascript
const username = "Aman";

const age = 20;

const city = "Ahmedabad";
```

Without adding logs you can inspect

```
username → Aman

age → 20

city → Ahmedabad
```

This makes debugging much faster.

---

# 👀 Watching Expressions

Sometimes you only care about one variable.

Instead of inspecting everything,

add a Watch Expression.

Example

```
count

user.name

isLoggedIn

response.data
```

Whenever execution pauses,

their current values are shown automatically.

---

# 🌐 Debugging API Calls

Suppose

```javascript
const response = await fetch(API_URL);

const data = await response.json();
```

Place a breakpoint before

```javascript
await response.json();
```

Inspect

- response.status
- response.headers
- response.ok

before processing data.

This helps detect API problems immediately.

---

# ⚛️ Debugging React State

Example

```javascript
const [count, setCount] = useState(0);
```

Breakpoint

```javascript
setCount(count + 1);
```

Inspect

```
count

props

state

hooks
```

before updating.

---

# 📦 Debugging Props

Example

```javascript
function Profile({ user }) {

}
```

Pause here.

Inspect

```
user

user.name

user.email
```

If the prop is undefined,

you know the issue is in the parent component.

---

# ⏳ Debugging Async Code

Example

```javascript
async function fetchData() {

    const response = await fetch(API_URL);

}
```

Breakpoints work before and after

```
await
```

making them ideal for asynchronous debugging.

---

# 🚦 Conditional Breakpoints

Sometimes a loop executes 1000 times.

Instead of stopping every iteration,

use a condition.

Example

```
count === 100
```

The debugger pauses only when the condition becomes true.

Very useful for large datasets.

---

# 🆚 Breakpoints vs console.log()

| Breakpoints | console.log() |
|-------------|---------------|
| Pause execution | Doesn't pause |
| Inspect everything | Only logs what you print |
| Cleaner | Can clutter code |
| No code changes | Requires editing code |
| Better for complex bugs | Better for quick checks |

---

# 💼 Real Example

Bug

```javascript
const user = undefined;

console.log(user.name);
```

Instead of adding

```javascript
console.log(user);
```

Place a breakpoint before

```javascript
user.name
```

Inspect

```
user
```

You'll immediately discover

```
undefined
```

without modifying your code.

---

# ❌ Common Mistakes

- Adding breakpoints everywhere.
- Forgetting to remove unnecessary breakpoints.
- Ignoring Watch Expressions.
- Never inspecting the Call Stack.
- Depending only on console.log().

---

# 💡 Best Practices

✅ Break at the source of the bug.

✅ Use Step Into to understand function calls.

✅ Use Step Over for simple functions.

✅ Watch important variables.

✅ Inspect state before changing it.

✅ Combine breakpoints with stack traces.

---

# 🎯 Practice Exercises

Exercise 1

Pause inside a button click handler.

Inspect

- props
- state
- local variables

---

Exercise 2

Pause before an API request.

Inspect

```
API_URL
```

Then continue.

---

Exercise 3

Pause after the response arrives.

Inspect

```
response

status

headers

data
```

---

Exercise 4

Create a conditional breakpoint inside a loop.

Pause only when

```
index === 5
```

---

# 📝 Summary

You learned

- What breakpoints are
- Why they're better than excessive console.log()
- Debug controls (Continue, Step Over, Step Into, Step Out)
- Watching expressions
- Inspecting variables
- Debugging React state
- Debugging props
- Debugging async code
- Conditional breakpoints
- Best practices

---

# 📚 Official Resources

- React Native DevTools
- Chrome DevTools Debugger
- Expo Debugging Documentation

---

# 🚀 Next Chapter

➡ **05-React-Native-DevTools.md**

In the next chapter, you'll learn the complete React Native DevTools interface, including the **Console**, **Components**, **Profiler**, **Network**, **Memory**, **Sources**, and **Performance** tabs, and how professional developers use them to debug real-world applications.