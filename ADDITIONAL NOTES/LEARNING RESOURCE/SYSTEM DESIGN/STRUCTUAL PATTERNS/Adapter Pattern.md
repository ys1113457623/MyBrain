The **Adapter Pattern** is a **structural design pattern** that allows two incompatible interfaces to work together. It acts as a **bridge** between two different systems or components that wouldn’t normally be able to communicate.

**When to Use the Adapter Pattern?**

• When integrating **legacy code** with a new system.
• When working with **third-party libraries** that don’t match your application’s expected format.
• When you need to **convert API responses** into a format your frontend can understand.
• When using **different data structures** that require a unified format.

**Real-World Analogy**
Think of an **electrical power adapter**. If you travel to a country with different plug types, your charger won’t fit into the socket. The adapter **converts** your charger’s plug into the correct format so it can work with the new power outlet.

Similarly, in programming, an **adapter takes one interface and converts it into another** so they can work together.

**Adapter Pattern in JavaScript**
Let’s assume we have **an old API** that returns user data in a different format than what our new system expects.

  **Example: Adapting API Data Format**

```javascript
// Old API Response (incompatible format)
const oldApiResponse = {
  first_name: "John",
  last_name: "Doe",
  user_age: 30
};

// Adapter to convert old API response into new format
class UserAdapter {
  constructor(oldUser) {
    this.fullName = `${oldUser.first_name} ${oldUser.last_name}`;
    this.age = oldUser.user_age;
  }
}

// Using the adapter
const adaptedUser = new UserAdapter(oldApiResponse);
console.log(adaptedUser);
```

**Output:**

```
{
  "fullName": "John Doe",
  "age": 30
}
```

Here, UserAdapter transforms first_name and last_name into fullName and renames user_age to age, ensuring compatibility.

**Adapter Pattern in React**
In React, the Adapter Pattern is useful when wrapping third-party components or normalizing API data.

**Example: Adapting a Third-Party Button Component**
Imagine a UI library provides a button component with a different prop structure than what your project requires.

```javascript
import React from "react";

// Third-party button component (incompatible)
const ThirdPartyButton = ({ bgColor, label }) => {
  return <button style={{ backgroundColor: bgColor }}>{label}</button>;
};

// Adapter component to match our expected format
const ButtonAdapter = ({ color, text }) => {
  return <ThirdPartyButton bgColor={color} label={text} />;
};

// Usage
export default function App() {
  return <ButtonAdapter color="blue" text="Click Me" />;
}
```

Here, the ButtonAdapter converts color → bgColor and text → label, making the third-party button work seamlessly in our app.

**Adapter Pattern in Redux**

When working with APIs in **Redux**, we often get responses in different formats. The Adapter Pattern helps normalize API data before storing it in the state.

**Example: Normalizing API Data in Redux**

```javascript
// API Response
const apiResponse = {
  user_id: 101,
  user_name: "Alice",
  user_email: "alice@example.com"
};

// Adapter Function to normalize data
const normalizeUser = (data) => ({
  id: data.user_id,
  name: data.user_name,
  email: data.user_email
});

// Redux Reducer
const userReducer = (state = {}, action) => {
  switch (action.type) {
    case "SET_USER":
      return normalizeUser(action.payload); // Applying the adapter
    default:
      return state;
  }
};

// Usage in Action Dispatch
const userData = normalizeUser(apiResponse);
console.log(userData);
```

**Output:**

```
{
  "id": 101,
  "name": "Alice",
  "email": "alice@example.com"
}
```

Here, the normalizeUser() function acts as an **adapter**, ensuring our Redux store has a consistent data structure.

**Adapter Pattern vs. Other Patterns**

|**Pattern**|**Purpose**|**Example**|
|---|---|---|
|**Adapter**|Converts an existing interface into a compatible one|Adapting an API response for frontend use|
|**Facade**|Provides a simpler interface to a complex system|Wrapping multiple API calls into one function|
|**Decorator**|Enhances an object’s behavior dynamically|Adding logging to API requests|
|**Proxy**|Controls access to an object|Lazy-loading images in a gallery|

**When Not to Use the Adapter Pattern?**

• When modifying the original code is possible (instead of adapting it).
• When performance is a concern (adapters add a layer of abstraction).
• When a **Facade Pattern** would be more suitable (simplifying rather than adapting).

**Final Thoughts**
• The **Adapter Pattern** is great for **integrating incompatible systems**.
• It helps when dealing with **legacy code, third-party libraries, and API response transformations**.
• It is **widely used in JavaScript and React** for UI components, Redux state management, and API data handling.