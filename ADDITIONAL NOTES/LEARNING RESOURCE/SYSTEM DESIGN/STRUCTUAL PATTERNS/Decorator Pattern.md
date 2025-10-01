The **Decorator Pattern** is a **structural design pattern** that allows behavior to be **dynamically added** to individual objects **without modifying their code**. It is an **alternative to subclassing**, making it more flexible for extending functionality.

---

**When to Use the Decorator Pattern?**

• When you need to **add functionality dynamically** to objects at runtime.

• When you want to **avoid subclassing**, which can lead to complex inheritance trees.

• When you need to **apply multiple behaviors** to objects (e.g., UI enhancements, logging, caching).

• When you want to **modify an object’s behavior without altering its structure**.

---

**Real-World Analogy**

  

Imagine ordering a **coffee**. A basic coffee costs $5. If you want **milk**, it adds $2. If you also want **sugar**, it adds $1.

  

Instead of modifying the **base coffee class** to include all possible add-ons, we use a **decorator** to wrap the coffee and dynamically enhance it.

---

**Decorator Pattern in JavaScript**

  

Let’s implement a **coffee order system**, where we can decorate a base coffee with additional features.

  

**Example: Coffee Order System**

```
// Step 1: Base Coffee Class (Component)
class Coffee {
  cost() {
    return 5;
  }
}

// Step 2: Decorator - Adds Milk
class MilkDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 2; // Adds milk cost
  }
}

// Step 3: Decorator - Adds Sugar
class SugarDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 1; // Adds sugar cost
  }
}

// Step 4: Usage
let myCoffee = new Coffee();
console.log("Plain Coffee: $" + myCoffee.cost()); // $5

myCoffee = new MilkDecorator(myCoffee);
console.log("Coffee with Milk: $" + myCoffee.cost()); // $7

myCoffee = new SugarDecorator(myCoffee);
console.log("Coffee with Milk and Sugar: $" + myCoffee.cost()); // $8
```

**Output:**

```
Plain Coffee: $5
Coffee with Milk: $7
Coffee with Milk and Sugar: $8
```

**How It Works?**

• **Base Class (Coffee)** defines the core behavior.

• **Decorator Classes (MilkDecorator, SugarDecorator)** wrap the base class and add features.

• **Each decorator extends the object’s behavior without modifying the original class**.

---

**Decorator Pattern in React**

  

In **React**, the **Decorator Pattern** is commonly used for **Higher-Order Components (HOCs)**.

  

**Example: Adding Logging to a Button Component**

```
import React from "react";

// Step 1: Base Component
const Button = ({ onClick, label }) => {
  return <button onClick={onClick}>{label}</button>;
};

// Step 2: Decorator (HOC) - Adds Logging Behavior
const withLogging = (WrappedComponent) => {
  return (props) => {
    const handleClick = () => {
      console.log(`Button Clicked: ${props.label}`);
      if (props.onClick) {
        props.onClick();
      }
    };

    return <WrappedComponent {...props} onClick={handleClick} />;
  };
};

// Step 3: Using the Decorated Component
const ButtonWithLogging = withLogging(Button);

export default function App() {
  return <ButtonWithLogging label="Click Me" />;
}
```

**How It Works?**

• **Button is the base component.**

• **withLogging is a decorator (HOC) that adds logging functionality.**

• **ButtonWithLogging is the enhanced component that logs clicks.**

---

**Decorator Pattern in Middleware (Redux)**

  

Redux **middleware** follows the **Decorator Pattern**, wrapping actions with additional behavior.

  

**Example: Logging Middleware in Redux**

```
const loggerMiddleware = (store) => (next) => (action) => {
  console.log("Dispatching:", action);
  let result = next(action);
  console.log("Next State:", store.getState());
  return result;
};

// Applying middleware
const store = createStore(reducer, applyMiddleware(loggerMiddleware));
```

**How It Works?**

• The **loggerMiddleware** wraps around Redux actions.

• It **logs** every dispatched action without modifying the Redux store itself.

---

**Decorator Pattern vs Other Patterns**

|**Pattern**|**Purpose**|**Example**|
|---|---|---|
|**Decorator**|Dynamically adds behavior to objects|HOCs in React, Redux middleware|
|**Adapter**|Converts an interface into another compatible one|API response transformation|
|**Composite**|Treats individual and group objects uniformly|Tree structures like menus|
|**Proxy**|Controls access to an object|API request caching|

  

---

**When Not to Use the Decorator Pattern?**

• If modifications can be **done via subclassing** without excessive inheritance.

• When a **simple function or utility** can add behavior instead.

• When you don’t need **runtime flexibility** (decorators are useful when behaviors change dynamically).

---

**Final Thoughts**

• The **Decorator Pattern** is perfect for **adding functionality dynamically**.

• It is widely used in **React (HOCs), Redux middleware, and UI enhancements**.

• It helps keep code **modular, reusable, and flexible**.

  

Would you like me to compare this pattern with **Proxy or Composite Pattern** for deeper understanding? 🚀