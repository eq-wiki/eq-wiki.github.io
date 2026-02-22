title: Guide
order: 2

Hey there! 👋 Welcome to the world of **Kavo**. This guide will help you get started with creating documents in Kavo, without drowning in boring formal rules. Think of this as a friendly walkthrough.

## Properties

Properties are the basic building blocks. They store values inside sections or at the top level.

**Example:**

```kavo
username: "Stargazer127"
age: 18
isAdmin: true
favoriteNumbers: [3 7 42]
```

!!! info "**Tip:**"
    Properties can be required (`!`) or optional (`?`), but don't stress — you'll pick it up quickly.

## Sections

Sections are like **containers** or “folders” for your properties, functions, and other stuff.

**Example:**

```kavo
User {
    username: "Jonas"
    age: 18
    isAdmin: true
}
```

You can even nest sections:

```kavo
App {
    User {
        username: "Jonas"
    }
    Settings {
        theme: "dark"
    }
}
```

Think of sections as grouping things together — keeps your document organized.


## Functions

Functions let you define **blocks of code or data**. They don't run automatically — you decide when and how to use them in your runtime.

**Example:**

```kavo
greet(name) {
    return "Hello " + name + "!"
}

logSomething() js {
    console.log("Hello from JavaScript")
}
```

You can even specify the language if you want — JS, Python, GLSL, or whatever your runtime understands.

## Lists

Lists are just **collections of values**. Easy to create and easy to read.

**Example:**

```kavo
favoriteColors: ["red" "green" "blue"]
numbers: [1 2 3 4 5]
```

## Macros

Macros are special instructions for the compiler. They **don't run at runtime**, but they can help with tasks like importing files or validating data.

**Common macros:**

```kavo
#import "common.kavo"      // bring in another file
#merge "theme.kavo"       // bring in a file, overwrite duplicates
#validate { ... }         // check your data
```

## Validate

Validate is a special macro that lets you validate your data and has a special syntax.

**Example:**

```kavo
#validate {
    require self.isExtended // checks if the section is extended

    self has radius // checks if a property exists
    :> "Button must have a radius"

    text matches "^[a-zA-Z\s_\-]+$" // regex
    :> "Text must be alphanumeric"

    radius is number or string // can be a number or a string
    :> "Radius must be a number, but was: {radius.type}"

    radius >= 0 // must be positive
    :> "Radius must be positive, but was: {radius.value}"
}
```

## Inheritance

Inheritance lets you **reuse sections** and override properties — like copying a template and tweaking it.

**Example:**

```kavo
Rectangle {
    width: 10
    height: 10
}
Square extends Rectangle {
    width: 20
}
```

The `Square` section now has all the stuff from `Rectangle`, but width is overridden.

## Decorators

Decorators are **extra labels** you can attach to sections. They add meaning, like “this is unstable” or “this is release-ready.”

**Example:**

```kavo
@kavo(1.0)           // version decorator
@decorator "yes, please!" // decorator with a message
@unstable;            // unstable decorator
@releaseReady;       // release-ready decorator
```

!!! warning "🚨 Warning:"
    If you want to have a decorator without value (returns truthy decorator) you have to add a `;` at the end of the decorator.

!!! info "💡 Tip:"
    Don't worry too much at first — decorators are just metadata.

## Comments

Comments are ignored by Kavo. Use them to leave notes for yourself or others.

```kavo
// This is a single-line comment
/* This is a multi-line comment */
```


## Whitespace & Newlines

* Kavo mostly ignores spaces and newlines.
* Use **indentation** to make your document easier to read.
* Inside strings, spaces and newlines **are preserved**.

```kavo
section {
    prop: hello
    prop: world
}
```

is the same as:

```kavo
section { prop: hello prop: world }
```

## That's It!

And that's your quick-start guide! 🎉

* Start with **properties** and **sections**.
* Add **functions** and **lists** as needed.
* Use **macros** and **inheritance** for reusable patterns.
* Decorators and comments help keep things organized.

Have fun building with Kavo! 🚀s