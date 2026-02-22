title: About
order: 1

# Kavo

**Kavo** is a declarative, hierarchical format for defining **modular data and component structures**. It provides a consistent way to describe objects, values, properties, arguments, and nested elements in a format that is **both human-readable and machine-interpretable**.

While Kavo is used internally in **Aureli OS plugins**, it is a **general-purpose format** that can be applied to any system requiring structured, reusable component definitions.

## Overview

Kavo organizes information as **Nodes**, each representing a logical unit or component. Nodes are self-contained and can include:

* A name and type
* Arguments or parameters
* An optional value
* Optional metadata properties
* Nested child nodes

This makes Kavo ideal for **hierarchical, modular designs** where clarity and extensibility are important.

## Hierarchical Structure

Kavo encourages **tree-like compositions**. Nodes can contain child nodes, which can themselves have children. This structure allows **modular, reusable, and composable systems**, supporting patterns such as:

```
Root Node
├─ Child Node A
│  ├─ Nested Node A1
│  └─ Nested Node A2
└─ Child Node B
   └─ Nested Node B1
```

- Each child is a **node**
- Each node can define its **value, arguments, properties, and children**
- Hierarchy is flexible and can be arbitrarily deep

---

## Usage Patterns

Kavo can be used for:

1. **UI Components:** Defining panels, widgets, or controls in a modular way
2. **Data Structures:** Representing configuration, state, or system metadata
3. **Reusable Modules:** Sharing and composing nodes across different systems
4. **Dynamic Computation:** Arguments and values allow nodes to interact or adapt at runtime

!!! info "Note:"
    Aureli OS plugins are built using Kavo as the underlying component format. A typical plugin defines metadata, configuration, event handlers, and widgets using Kavo’s structured approach. However, Kavo is not limited to Aureli OS plugins—it can be applied wherever modular, hierarchical component definitions are needed.


## Conceptual Example

A conceptual representation of a Kavo node tree:

```
Plugin Node
├─ Meta (name, version, author)
├─ Config (defaults, values)
├─ Event Handlers
│  ├─ onLoad
│  └─ onRender
└─ Widgets
   ├─ Widget A
   │  ├─ Meta
   │  └─ Render Logic
   └─ Widget B
       ├─ Meta
       └─ Render Logic
```

Each node is **self-contained** and **flexibly composable**, supporting clear and maintainable systems.
