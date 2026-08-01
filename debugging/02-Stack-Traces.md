# 📚 Stack Traces

> Learn how to read, understand, and use stack traces to quickly locate and fix errors in React Native applications.

---

# 📖 Table of Contents

- Introduction
- What is a Stack Trace?
- Why Stack Traces Matter
- How a Stack Trace is Created
- Anatomy of a Stack Trace
- Reading a Stack Trace
- Understanding File Names & Line Numbers
- Following the Call Stack
- Real Examples
- Common Mistakes
- Best Practices
- Practice Exercises
- Summary
- Resources

---

# 📚 Introduction

Imagine your application crashes and all you see is:

```

TypeError:
Cannot read property 'name' of undefined

```

At first glance, this tells you **what** went wrong, but not necessarily **where**.

That's where a **stack trace** becomes one of the most powerful debugging tools.

A stack trace is a detailed report showing the sequence of function calls that led to an error. It helps you trace the execution path of your application so you can locate the exact source of the problem.

Instead of guessing, you can follow the stack trace directly to the offending file and line number.

---

# 🤔 What is a Stack Trace?

A stack trace is a list of function calls that were active when an error occurred.

Think of it as a breadcrumb trail.

Every time your application calls a function, JavaScript places that function on a structure called the **Call Stack**.

When an error occurs, React Native records that stack and displays it.

This lets you answer questions like:

- Which function caused the error?
- Which component was rendering?
- Which file contains the bug?
- Which line should I inspect first?

---

# 🧠 Think of It Like This

Imagine you're climbing stairs.

```

main()
↓
loadUser()
↓
fetchProfile()
↓
renderProfile()
↓
❌ Error

```

To understand why the error happened, you walk back up the same stairs.

That's exactly what a stack trace shows.

---

# 📦 How a Stack Trace is Created

Suppose you have:

```javascript
function third() {
  throw new Error("Something went wrong");
}

function second() {
  third();
}

function first() {
  second();
}

first();
```

Execution order:

```

first()
↓
second()
↓
third()
↓
❌ Error

```

Stack Trace:

```

Error: Something went wrong

at third()
at second()
at first()

```

Notice how JavaScript shows the path that led to the crash.

---

# 📄 Anatomy of a Stack Trace

A typical React Native stack trace contains several parts.

Example:

```

TypeError:
Cannot read property 'name' of undefined

at ProfileScreen (ProfileScreen.js:27)
at renderWithHooks
at updateFunctionComponent
at beginWork

```

Let's break it down.

---

## Error Type

```

TypeError

```

This tells you the category of error.

Examples include:

- TypeError
- ReferenceError
- SyntaxError
- RangeError

---

## Error Message

```

Cannot read property 'name' of undefined

```

This explains what actually happened.

---

## File Name

```

ProfileScreen.js

```

The file where the error originated.

---

## Line Number

```

27

```

The exact line to inspect first.

---

## Function Name

```

ProfileScreen()

```

Shows which function or component was executing.

---

# 🔍 Reading a Stack Trace

When you see a stack trace, don't panic.

Read it from the top.

Example:

```

ReferenceError:
username is not defined

App.js:18

```

This tells you:

- File → App.js
- Line → 18
- Error → username doesn't exist

Open **App.js**.

Go directly to line **18**.

Inspect the code around that line.

---

# ⚠️ Don't Read Every Line

Many beginners scroll through the entire stack trace and get confused.

React Native often includes internal framework functions like:

```

renderWithHooks
beginWork
performUnitOfWork

```

These are React internals.

Focus first on **your own files**, not React's internal implementation.

---

# 💻 Example 1

```javascript
export default function App() {
  return <Text>{username}</Text>;
}
```

Output:

```

ReferenceError:
Can't find variable: username

App.js:6

```

Diagnosis:

- username wasn't declared.

Fix:

```javascript
const username = "Aman";

export default function App() {
  return <Text>{username}</Text>;
}
```

---

# 💻 Example 2

```javascript
const user = undefined;

console.log(user.name);
```

Output:

```

TypeError:
Cannot read property 'name' of undefined

App.js:9

```

Diagnosis:

`user` is undefined.

Fix:

```javascript
if (user) {
  console.log(user.name);
}
```

---

# 💻 Example 3

```javascript
function divide(a, b) {
  return a / b;
}

divide(10);
```

The stack trace may point you to the function where invalid arguments were passed, helping you identify incorrect usage.

---

# 🖼️ Screenshot

Add a screenshot showing:

```

images/stacktrace.png

```

The screenshot should highlight:

- Error type
- File
- Line number
- Stack trace

---

# 🚀 How Professional Developers Read Stack Traces

Instead of reading everything:

1. Read the error type.
2. Read the message.
3. Open the first file that belongs to your project.
4. Ignore React Native internal functions at first.
5. Fix the issue.
6. Reload the app.
7. Repeat if another error appears.

---

# ❌ Common Mistakes

- Ignoring the line number.
- Reading only the error message.
- Blaming React Native.
- Editing random files without understanding the issue.
- Ignoring the first user-defined file in the stack.

---

# 💡 Best Practices

- Always start with the first error.
- Read the stack trace before searching online.
- Use breakpoints to inspect variables.
- Keep functions small so stack traces are easier to understand.
- Learn common JavaScript error types.

---

# 🎯 Practice Exercise

## Exercise 1

Create:

```javascript
const person = undefined;

console.log(person.age);
```

Observe:

- Error type
- File
- Line number
- Stack trace

Then fix it.

---

## Exercise 2

Create three nested functions.

Throw an error inside the deepest function.

Observe how the stack trace changes.

---

# 📝 Summary

You now know:

- What a stack trace is
- How React Native creates stack traces
- How to read them
- How to locate files and line numbers
- Which parts of the stack trace matter most
- Common mistakes to avoid

---

# 📚 Official Resources

- React Native Debugging Documentation
- Expo Debugging Documentation
- JavaScript Error Reference (MDN)

---

## 🚀 Next Chapter

➡️ **03-Console-Debugging.md**

You'll learn how to use `console.log()`, `console.warn()`, `console.error()`, `console.table()`, `console.time()`, and other console methods effectively to debug React Native applications.