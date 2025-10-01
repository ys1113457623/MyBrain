˜The **Prototype Pattern** is a **creational design pattern** that allows us to create new objects by copying an existing object (prototype) instead of creating them from scratch. This approach improves performance and provides a flexible way to create object instances.

**When to Use the Prototype Pattern?**

• When object creation is **expensive (resource-intensive)** and cloning an existing object is more efficient.

• When you want to **preserve object structure** but modify certain properties.

• When working with **complex objects** where manual duplication would be cumbersome.

• When you need **prototypes for multiple object instances** (e.g., game objects, UI components, form templates).

**Real-World Analogy**

Think of a **rubber stamp**. Instead of drawing a logo manually every time, you **copy** the design using the stamp. The original stamp (prototype) remains the same, and you create multiple identical copies by stamping it.

Similarly, in programming, we create an object from an existing object (prototype) rather than building it from scratch.

**Prototype Pattern in JavaScript**

JavaScript natively supports the Prototype Pattern through **prototypes and Object.create()**.

**Example: Cloning an Object Using Prototype**

```javascript
// Step 1: Define a Prototype Object
const carPrototype = {
  init(brand, model, color) {
    this.brand = brand;
    this.model = model;
    this.color = color;
  },
  clone() {
    return Object.create(this);
  },
  showDetails() {
    console.log(`Car: ${this.brand} ${this.model}, Color: ${this.color}`);
  }
};

// Step 2: Create a New Object by Cloning
const car1 = carPrototype.clone();
car1.init("Toyota", "Camry", "Red");
car1.showDetails();

const car2 = carPrototype.clone();
car2.init("Honda", "Civic", "Blue");
car2.showDetails();
```

**Output:**

```
Car: Toyota Camry, Color: Red
Car: Honda Civic, Color: Blue
```

**How It Works?**

1. **carPrototype acts as a blueprint (prototype).**
2. **clone() creates a shallow copy of the prototype.**
3. **Each new object (e.g., car1, car2) initializes its properties separately.**

**Prototype Pattern Using Classes**

With ES6 **class-based syntax**, we can implement the Prototype Pattern using the clone() method.

```javascript
class Car {
  constructor(brand, model, color) {
    this.brand = brand;
    this.model = model;
    this.color = color;
  }

  clone() {
    return new Car(this.brand, this.model, this.color);
  }

  showDetails() {
    console.log(`Car: ${this.brand} ${this.model}, Color: ${this.color}`);
  }
}

// Creating a prototype instance
const carPrototype = new Car("Tesla", "Model S", "Black");

// Cloning new instances
const car1 = carPrototype.clone();
car1.color = "Red"; // Modifying cloned instance
car1.showDetails();

const car2 = carPrototype.clone();
car2.color = "Blue";
car2.showDetails();
```

**Output:**

```
Car: Tesla Model S, Color: Red
Car: Tesla Model S, Color: Blue
```

Here, car1 and car2 were cloned from carPrototype, but they have different colors.

**Prototype Pattern in React**

React components often use the Prototype Pattern when duplicating UI elements with shared properties.

**Example: Cloning a React Component**

In React, the React.cloneElement() method allows us to clone an existing component and modify its properties.

```javascript
import React from "react";

const Button = ({ color, text }) => {
  return <button style={{ backgroundColor: color }}>{text}</button>;
};

const OriginalButton = <Button color="blue" text="Click Me" />;

// Cloning and modifying the component
const ClonedButton = React.cloneElement(OriginalButton, { color: "red", text: "Submit" });

export default function App() {
  return (
    <div>
      {OriginalButton}
      {ClonedButton}
    </div>
  );
}
```

Here, React.cloneElement() creates a copy of the original button but with different properties.

**Shallow Copy vs Deep Copy in Prototypes**

• **Shallow Copy:** Copies only references, so changes in the original object affect the cloned object.

• **Deep Copy:** Creates a completely independent object.

**Shallow Copy Example (Reference-Based Copying)**

```javascript
const original = { name: "Alice", address: { city: "New York" } };
const copy = Object.create(original);

copy.address.city = "Los Angeles"; // Modifies both original and copy

console.log(original.address.city); // "Los Angeles"
```

**Deep Copy Example (Independent Copying)**

```javascript
const original = { name: "Alice", address: { city: "New York" } };
const copy = JSON.parse(JSON.stringify(original));

copy.address.city = "Los Angeles"; // Modifies only copy

console.log(original.address.city); // "New York"
```

Use **deep copies** when you need fully independent objects.

**When Not to Use the Prototype Pattern?**

• When object creation is simple and doesn’t involve costly operations.

• When using ES6 **class-based inheritance** is sufficient.

• When working with primitive values (cloning is unnecessary).

**Final Thoughts**

• The **Prototype Pattern** is a powerful way to **clone objects** without direct instantiation.

• It improves **performance** by avoiding costly object creation.

• It is **commonly used in JavaScript** via Object.create(), class cloning, and React.cloneElement().

• Be mindful of **shallow vs deep copies** when working with nested objects.