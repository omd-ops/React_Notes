````md
# useState with Boolean Value

```jsx
import { useState } from "react";

export const LoginCard = () => {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  const handleLogin = () => {
    setIsLoggedIn(!isLoggedIn);
  };

  return (
    <button onClick={handleLogin}>
      {isLoggedIn ? "Logout" : "Login"}
    </button>
  );
};
```

## Explanation

- `isLoggedIn` stores a boolean value (`true` or `false`)
- Initial value is `false`
- Clicking the button toggles the value using:

```jsx
setIsLoggedIn(!isLoggedIn);
```

- Ternary operator is used to conditionally render:
  - `"Login"` when `false`
  - `"Logout"` when `true`

---

# useState with Empty String Value

```jsx
import { useState } from "react";

export const LoginCard = () => {
  const [message, setMessage] = useState("");

  const handleChange = (event) => {
    setMessage(event.target.value);
  };

  return (
    <div>
      <input
        type="text"
        placeholder="Type a message"
        value={message}
        onChange={handleChange}
      />

      <p>{message}</p>
    </div>
  );
};
```

## Explanation

- `message` stores text input from the user
- Initial value is an empty string:

```jsx
useState("");
```

- `onChange` runs whenever the input value changes
- `event.target.value` gets the current text inside the input field
- `setMessage()` updates the state
- React re-renders the component and displays the updated message

---

# Key Concepts

## Controlled Component

The input field is a controlled component because:

```jsx
value={message}
```

React controls the input value through state.

---

# Event Flow

1. User types in input
2. `onChange` event triggers
3. `handleChange` executes
4. `setMessage()` updates state
5. Component re-renders
6. Updated message appears on screen
````

