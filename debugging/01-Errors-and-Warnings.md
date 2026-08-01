# 🚨 Errors and Warnings

> Learn how React Native reports problems while developing your application.

---

# 📖 Table of Contents

- Introduction
- What is an Error?
- What is a Warning?
- Error vs Warning
- React Native LogBox
- RedBox Errors
- YellowBox Warnings
- Creating Your Own Errors & Warnings
- Fatal vs Non-Fatal Errors
- Common Error Types
- Reading Error Messages
- Best Practices
- Common Mistakes
- Practice Exercise
- Summary
- Resources

---

# 📚 Introduction

No matter how experienced you become, **you will always encounter errors** while developing applications.

Errors are not a sign that you're a bad developer.

In fact, professional developers spend a large part of their day reading error messages, understanding what went wrong, and fixing issues.

Learning **how to understand errors** is one of the most valuable skills you can develop.

React Native provides an excellent debugging experience by displaying detailed error messages directly on the screen during development.

Instead of crashing silently, React Native tells you:

- What went wrong
- Where it happened
- Which file caused the issue
- Which line number contains the problem
- The sequence of function calls that led to the error

Understanding this information will dramatically reduce the time you spend fixing bugs.

---

# 🤔 What is an Error?

An **error** is a problem that prevents your code from running correctly.

When JavaScript encounters an instruction that it cannot execute, it throws an error.

If that error isn't handled properly, React Native stops executing your application and displays a **RedBox**.

Think of an error as the application saying:

> "I don't know how to continue."

---

## Example

```javascript
const user = undefined;

console.log(user.name);
```

Output

```
TypeError:
Cannot read property 'name' of undefined
```

Since JavaScript cannot access the property `name` on an undefined value, execution stops.

---

# ⚠️ What is a Warning?

A warning is **not** an error.

Warnings tell you that something in your code **might cause problems** now or in the future.

Unlike errors, warnings **do not stop** your application.

Your app continues running normally.

Think of a warning as React Native saying:

> "Your code works, but you should fix this."

---

## Example

```javascript
console.warn("This API is deprecated.");
```

Output

```
Warning:
This API is deprecated.
```

The application still runs successfully.

---

# 🔍 Error vs Warning

| Error | Warning |
|--------|----------|
| Stops the app | App continues running |
| Must be fixed | Should be fixed |
| Displays RedBox | Displays YellowBox |
| Prevents execution | Only informs the developer |
| Usually caused by invalid code | Usually caused by bad practices |

---

# 📦 React Native LogBox

React Native uses **LogBox** to display messages during development.

LogBox makes debugging much easier by organizing:

- Errors
- Warnings
- Stack traces
- Code frames

Before LogBox, React Native used RedBox and YellowBox separately.

Modern React Native combines them into a cleaner debugging experience.

---

# 🔴 RedBox Error

A **RedBox** appears whenever your application encounters a **fatal JavaScript error**.

Because the JavaScript thread crashes, React Native cannot continue rendering your application.

Instead of showing a broken screen, React Native displays a full-screen error message called the **RedBox**.

---

## When does RedBox appear?

Common reasons include:

- Undefined variables
- Incorrect imports
- Invalid JSX
- Accessing null values
- Calling undefined functions
- Infinite recursion
- Unhandled exceptions

---

## Example

```javascript
export default function App() {
  return <Text>{username}</Text>;
}
```

Output

```
ReferenceError:
Can't find variable: username
```

Since `username` was never declared, React Native displays a RedBox.

---

### 📷 Screenshot

```
images/redbox.png
```

---

# 🟡 YellowBox Warning

YellowBox informs developers about possible problems.

Unlike RedBox, your application continues running.

Warnings help you improve your application before shipping it.

---

## Example

```javascript
console.warn("Deprecated API used.");
```

Output

```
Warning:
Deprecated API used.
```

---

### 📷 Screenshot

```
images/yellowbox.png
```

---

# 🧪 Creating Your Own Errors & Warnings

Sometimes you want to intentionally create warnings or errors while testing.

### Warning

```javascript
console.warn("Network request is taking too long.");
```

### Error

```javascript
console.error("Unable to fetch user profile.");
```

### Throw an Exception

```javascript
throw new Error("User authentication failed.");
```

This immediately triggers a RedBox if the error is not caught.

---

# 💥 Fatal vs Non-Fatal Errors

## Fatal Error

The application cannot continue.

Example:

```javascript
const user = undefined;

console.log(user.name);
```

Result

```
❌ App crashes
```

---

## Non-Fatal Error

The issue is handled gracefully.

Example

```javascript
try {
    throw new Error("Something went wrong");
} catch (error) {
    console.log(error.message);
}
```

Result

```
✅ App continues running
```

---

# 📖 Common Error Types

## ReferenceError

Occurs when a variable does not exist.

```javascript
console.log(username);
```

---

## TypeError

Occurs when JavaScript receives the wrong data type.

```javascript
const user = null;

console.log(user.name);
```

---

## SyntaxError

Occurs when your JavaScript syntax is incorrect.

```javascript
const name =
```

---

## RangeError

Occurs when a value exceeds the allowed range.

```javascript
const numbers = new Array(-1);
```

---

# 🧠 How to Read Error Messages

When React Native displays an error, don't immediately look at the code.

Instead, follow this order:

1. Read the error type.
2. Read the message.
3. Find the file name.
4. Go to the line number.
5. Read the stack trace.
6. Understand the root cause.
7. Fix the problem.

Most beginners skip the first five steps and start guessing.

Professional developers always read the error first.

---

# 💡 Best Practices

- Read the complete error message.
- Fix the first error before fixing others.
- Never ignore warnings.
- Don't blindly copy solutions from the internet.
- Try to understand why the error occurred.
- Use official documentation whenever possible.

---

# ❌ Common Mistakes

- Ignoring YellowBox warnings.
- Reading only the first line of the error.
- Panic-debugging by changing random code.
- Using `console.log()` everywhere instead of understanding the issue.
- Not reproducing the error consistently.

---

# 🎯 Practice Exercise

1. Create an undefined variable and observe the RedBox.
2. Display a warning using `console.warn()`.
3. Throw an error using `throw new Error()`.
4. Fix each issue and verify the application works again.

---

# 📝 Summary

After completing this chapter, you should understand:

- What errors are
- What warnings are
- The difference between RedBox and YellowBox
- Fatal vs non-fatal errors
- React Native LogBox
- Common JavaScript error types
- How to read error messages
- Basic debugging workflow

---

# 📚 Official Resources

- React Native Debugging Documentation
- Expo Debugging Documentation
- JavaScript Error Reference (MDN)

---

## 🚀 Next Chapter

➡️ **02-Stack-Traces.md**

You'll learn how to read stack traces like a professional developer and pinpoint the exact location of an error in seconds.