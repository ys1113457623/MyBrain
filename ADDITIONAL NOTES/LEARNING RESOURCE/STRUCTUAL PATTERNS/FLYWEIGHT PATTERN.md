The **Flyweight Pattern** is a **structural design pattern** that **optimizes memory usage** by **sharing common parts of objects** instead of creating multiple identical instances. It is useful when an application has a **large number of similar objects**.

---

**When to Use the Flyweight Pattern?**

• When you have **a large number of objects** that share common data.

• When **memory optimization** is a priority.

• When objects have **common intrinsic state** that can be shared.

• When object creation is **expensive in terms of memory**.

---

**Real-World Analogy**

  

**Text Editor (Font Sharing)**

  

When you write text in **Microsoft Word or Google Docs**, each character (A, B, C, etc.) **does not get a new object**. Instead, the font rendering system **reuses the same character representation** and only stores its position, size, and styling separately.

  

Instead of creating **1000 objects for the letter “A”**, the Flyweight Pattern **reuses one “A” object** and tracks different positions and styles.

---

**Flyweight Pattern in JavaScript**

  

Let’s consider an example where we **optimize a system that handles shapes**.

  

**Example: Optimizing Shape Objects**

```
// Step 1: Flyweight Factory (Manages Shared Objects)
class ShapeFactory {
  constructor() {
    this.shapes = {};
  }

  getShape(type, color) {
    const key = `${type}-${color}`;
    if (!this.shapes[key]) {
      console.log(`Creating new ${type} of color ${color}`);
      this.shapes[key] = new Shape(type, color);
    }
    return this.shapes[key];
  }

  getTotalShapes() {
    return Object.keys(this.shapes).length;
  }
}

// Step 2: Flyweight Object (Shared Object)
class Shape {
  constructor(type, color) {
    this.type = type;
    this.color = color;
  }

  draw(x, y) {
    console.log(`Drawing ${this.color} ${this.type} at (${x}, ${y})`);
  }
}

// Step 3: Usage
const shapeFactory = new ShapeFactory();

const shape1 = shapeFactory.getShape("Circle", "Red");
shape1.draw(10, 20);

const shape2 = shapeFactory.getShape("Circle", "Red"); // Reuses existing object
shape2.draw(30, 40);

const shape3 = shapeFactory.getShape("Square", "Blue");
shape3.draw(50, 60);

console.log("Total unique shapes created:", shapeFactory.getTotalShapes());
```

**Output:**

```
Creating new Circle of color Red
Drawing Red Circle at (10, 20)
Drawing Red Circle at (30, 40) // Reused object
Creating new Square of color Blue
Drawing Blue Square at (50, 60)
Total unique shapes created: 2
```

**How It Works?**

• **ShapeFactory** acts as a **flyweight factory**, ensuring **shapes are reused** instead of duplicated.

• If the same type and color exist, the factory **returns the existing instance** instead of creating a new one.

• This saves **memory** by preventing duplicate objects.

---

**Flyweight Pattern in React**

  

In **React**, the Flyweight Pattern is useful when dealing with **large lists of UI elements**, like a virtualized list where only visible items are rendered.

  

**Example: Optimizing a Large List with Flyweight (React Virtualization)**

  

Instead of rendering **1000+ DOM elements**, we only render **visible items**.

```
import React from "react";
import { FixedSizeList as List } from "react-window"; // React virtualization

// Large dataset (100,000 items)
const items = new Array(100000).fill(null).map((_, i) => `Item ${i + 1}`);

const Row = ({ index, style }) => (
  <div style={style} className="list-item">
    {items[index]}
  </div>
);

export default function App() {
  return (
    <List height={400} itemCount={items.length} itemSize={30} width={"100%"}>
      {Row}
    </List>
  );
}
```

**How It Works?**

• The Flyweight Pattern is **implemented via react-window**.

• Instead of rendering **100,000 items**, only **visible items** are rendered dynamically.

• This drastically **reduces memory usage and improves performance**.

---

**Flyweight Pattern in State Management**

  

If a frontend application stores **large datasets** in state (e.g., Redux, React Context), the Flyweight Pattern can be used to **avoid redundant data storage**.

  

**Example: Optimizing User Data Storage**

  

Imagine a system where we store **multiple users**, but most of them **share the same role**.

```
class Role {
  constructor(name, permissions) {
    this.name = name;
    this.permissions = permissions;
  }
}

class RoleFactory {
  constructor() {
    this.roles = {};
  }

  getRole(name, permissions) {
    if (!this.roles[name]) {
      this.roles[name] = new Role(name, permissions);
    }
    return this.roles[name];
  }

  getTotalRoles() {
    return Object.keys(this.roles).length;
  }
}

class User {
  constructor(name, role) {
    this.name = name;
    this.role = role; // Flyweight role
  }
}

// Usage
const roleFactory = new RoleFactory();

const adminRole = roleFactory.getRole("Admin", ["READ", "WRITE", "DELETE"]);
const userRole = roleFactory.getRole("User", ["READ"]);

const user1 = new User("Alice", adminRole);
const user2 = new User("Bob", userRole);
const user3 = new User("Charlie", adminRole); // Reuses admin role

console.log("Total unique roles:", roleFactory.getTotalRoles());
```

**Output:**

```
Total unique roles: 2
```

**How It Works?**

• **Instead of storing separate role objects for each user**, we reuse **pre-existing roles**.

• This **reduces memory usage**, especially when dealing with thousands of users.

---

**Flyweight Pattern vs Other Patterns**

|**Pattern**|**Purpose**|**Example**|
|---|---|---|
|**Flyweight**|Optimizes memory by sharing objects|UI virtualization, caching roles|
|**Prototype**|Clones objects instead of creating from scratch|Cloning UI components|
|**Singleton**|Ensures only one instance exists|Global configuration management|
|**Factory**|Creates objects without exposing logic|Object creation based on conditions|

  

---

**When Not to Use the Flyweight Pattern?**

• If objects **don’t share common data** (Flyweight is useful only for **shared state**).

• If **object creation is cheap and does not consume much memory**.

• If using **a caching mechanism** is sufficient for the use case.

---

**Final Thoughts**

• The **Flyweight Pattern** is ideal for **memory optimization** in **large-scale applications**.

• It is widely used in **frontend frameworks like React** for **virtualized lists, caching, and state management**.

• It **reduces object duplication** and improves **performance**.

  

Would you like me to compare this pattern with **Prototype or Factory Pattern** for a deeper understanding? 🚀