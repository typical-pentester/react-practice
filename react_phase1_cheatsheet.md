# 🥋 ReactSensei: Phase 1 Cheat Sheet

## 1. Components & JSX
A React component is just a JavaScript function that returns a Virtual DOM object (disguised as HTML using JSX).
- **Rule:** Component names *must* be Capitalized (e.g., `ProfileCard`, not `profileCard`).
- **Rule:** You must return only *one* parent element. Use a Fragment `<></>` if you need to wrap multiple elements without adding useless `<div>`s to the actual DOM.

```jsx
const WelcomeBanner = () => {
  return (
    <>
      <h1>Welcome!</h1>
      <p>Glad you are here.</p>
    </>
  );
};
```

## 2. Props (Object Destructuring)
**Props** are how you pass data *into* a component. They are read-only (immutable).
- **Mental Model:** Like DNA passed from a parent. You can't change it, you just inherit it.
- **Syntax Pattern:** Use Object Destructuring `{ }` in the function parameters to unpack the data instantly.

```jsx
// Destructuring { name, age } directly from the single props object
const UserCard = ({ name, age }) => {
  return <div>{name} is {age} years old.</div>;
};

// Passing props from the outside:
// <UserCard name="Shareef" age={25} />
```

## 3. State (Array Destructuring)
**State** is how a component remembers data that changes over time. When state changes, React automatically redraws the component.
- **Mental Model:** The component's personal notebook.
- **Syntax Pattern:** Use Array Destructuring `[ ]` to unpack the current value (index 0) and the updater function (index 1).

```jsx
import { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0); // 0 is the initial value

  return (
    <button onClick={() => setCount(count + 1)}>
      Clicked {count} times
    </button>
  );
};
```

## 4. Controlled Inputs (Forms)
To read what a user types, we tie the HTML `<input>` directly to our React `state`. The state becomes the "Single Source of Truth."

```jsx
const NameForm = () => {
  const [name, setName] = useState("");

  return (
    <input 
      value={name} // 1. The input reads its text from State
      onChange={(event) => setName(event.target.value)} // 2. Typing updates State
      placeholder="Enter your name" 
    />
  );
};
```
