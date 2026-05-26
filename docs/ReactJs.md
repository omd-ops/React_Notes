````md
# React Notes

## Props
Components share data with other components (used for parent-to-child communication).

### 1. Default Props
Default props are only used when the value is `undefined` or missing.

- If `null` or `0` is passed, the default value will **not** be used.

---

### 2. Forwarding Props with Spread Operator
```jsx
{...props}
```

### Rest Operator
```jsx
{...rest}
```

---

### 3. Passing JSX as Children
It is natural to nest elements inside each other.

Common use cases:
- Layouts
- Cards
- Modals

---

# Conditional Rendering

Conditional rendering is how components show different UI based on different conditions.

Example:
- Show login button if user is not logged in.

## Methods of Conditional Rendering

### 1. If Statements
Great for:
- Completely different renders
- Returning `null`

### 2. Ternary Operator (`?:`)
Perfect for:
- Either/or situations

### 3. AND Operator (`&&`)
Ideal for:
- Show/hide scenarios

### 4. Variables
Best for:
- Complex logic that makes JSX messy

### 5. Activity Component (React 19.2)
Used to:
- Hide parts of UI without removing them from the DOM

---

# Rendering Lists

## Key Prop
```jsx
key={crypto.randomUUID()}
```

---

# Event Handling

Event handling is all about passing functions to special props like `onClick`.

## Steps

### Step 1
Define a function that executes when the event occurs.

### Step 2
Assign the function to a special prop that starts with `on`.

Examples:
- `onChange` → inputs
- `onSubmit` → forms
- `onMouseEnter` → hovering
- `onClick` → buttons

---

## Example

```jsx
export const CustomButton = () => {
  const handleClick = () => {
    alert("Thanks for liking");
  };

  return <button onClick={handleClick}>Like</button>;
};
```

### Inline Alternative

```jsx
return (
  <button onClick={() => alert("Thanks for liking")}>
    Like
  </button>
);
```

---

## Important Note

When an event handler is passed:

```jsx
onClick={handleClick}
```

We pass the function **without `()`**.

### Wrong

```jsx
onClick={handleClick()}
```

This immediately executes the function during render, which is incorrect.

✅ We pass a function, not call it.

---

# Event Handling Using Props

Used for:
- Child-to-parent communication

We pass event handlers as props.

---

# State

## Props vs State

### Props
- Like arguments passed to a function
- Come from outside
- Cannot be changed by the component

### State
- Like a component's personal memory
- Belongs to the component
- Can be changed by the component itself

State makes React components interactive.

Without state:
- We are basically creating fancy HTML templates

With state:
- We build real-world applications

---

# When Do We Need State?

Ask these questions:

- Does this data need to change over time?
- Should the UI update when this data changes?
- Does the component need to remember this between renders?

---

# Hooks

Hooks are used to add state and other React features to components.

The most important hook for managing state is:

```jsx
useState
```

---

# useState Example

```jsx
import { useState } from "react";

export const Counter = () => {
  const [count, setCount] = useState(0);

  // Array destructuring

  console.log("Counter component rendered with count:", count);

  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <button onClick={handleClick}>
      Count: {count}
    </button>
  );
};
```

---

## How `useState` Works

`useState(initialValue)`:
- Accepts an initial value or a function
- Returns:
  1. Current state value
  2. Setter function

```jsx
const [currentValue, setterFunction] = useState(initialValue);
```

---

# What Happens When `setCount` Runs?

1. React updates the state value
2. React re-renders the component
3. `useState` gives the new value
4. UI updates automatically

---

# Lazy Initialization

Scenario when `useState` receives a function:

```jsx
useState(() => expensiveCalculation())
```

React calls this function:
- Only on the initial render
- Not on every re-render

---

## Useful For

- Expensive computations
- Reading from local storage
- Fetching initial data
- Heavy calculations

---

# Key Points About State

- Import `useState` from React
- Call it with an initial value
- You can also pass a function for lazy initialization
- Use array destructuring
- Use the state value inside JSX
- Use the setter function to update state
- Updating state triggers a re-render
- Components can have multiple state variables
- Multiple component instances each have their own local state

---

# Two Golden Rules of Hooks

## 1. Only Call Hooks at the Top Level

Hooks must be called:
- Directly inside the component function
- Before any conditions or returns

### ❌ Do NOT call hooks:
- Inside loops
- Inside nested functions
- Inside `if` statements
- Inside `try/catch`
- After early returns

---

## 2. Only Call Hooks from React Functions

Hooks can only be called from:
- React components
- Custom hooks

````

