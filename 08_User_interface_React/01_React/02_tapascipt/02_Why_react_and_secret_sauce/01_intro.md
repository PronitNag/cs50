# What is React?

**React** is a **declarative**, **component-based**, **JavaScript library** for building **user interfaces**.

---

## What is Declarative?

In **declarative programming**, you describe **what** you want to do but do **not specify how** it is done.

---

## What is Imperative?

In **imperative programming**, you describe **what** you want to do **by specifying all the instructions** on **how** to do it.

---

## But how can we prove that React is Declarative?

**Notice**:
- We don't have any `<ul>` elements in the JSX.
- There is no use of `getElementById()`.

Yet, the list appears in the UI.

This means React handles **DOM manipulation** by itself — it provides a **layer of abstraction** so that developers can focus on the **business logic**.

---

## What is a Component?

A **component** is an **isolated unit** that contains:

- Logic  
- Presentation logic  
- API integration  

### Benefits:

- One component can be **developed** and **tested** in isolation.
- Multiple components can be **integrated** and tested together.
- Each developer can work independently on their own component.

![component](https://github.com/user-attachments/assets/409018c2-a7ee-4ae7-b60d-a9c8c94fa63b)

We also pay attention to the **hierarchy** of components.

---

## Why is React a Library, Not a Framework?

A **library** focuses on **one thing**.  
A **framework** handles **multiple aspects** of an application.

React was created to solve **single-page interface** development problems.

To be considered a **framework**, React would need:

1. Theming  
2. Inbuilt Routing  
3. Inbuilt Testing  
4. Data Fetching (we use libraries like `axios`)  
5. Build Tools (e.g., `webpack`, `parcel`)  
6. State Management (e.g., `Redux`)  
7. Notifications  
8. And more...

> ✅ To do anything beyond the UI layer, we usually need to bring in **additional libraries**.

---
