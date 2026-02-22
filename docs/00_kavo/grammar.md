order: 3
title: Grammar

## 0. Dictionary

0.1 Dictionary rules:
* `[...]?` — question mark makes it optional

0.2 Grammar rules:
* optional `[type]` — `(int)`, `(string)`, `(list<str>)`, etc.
* optional `[flag]` — `!`, `?`, etc.
    * `!` — required
    * `?` — optional
* `[value]` — boolean, number, string, list, or empty (`;`)

## 0.3 Notes:

## 1. Document Structure

1.1 A Kavo document consists of:

* Optional **decorators** at the top (`@kavo(version)`) e.g. `@kavo(1.0)`
* One or more **statements** (sections, properties, functions, decorators, inheritance, macros)

1.2 Statements can be:

* Section
* Property
* Function
* Decorator
* Inheritance
* Macro

## 2. Decorators

2.1 Syntax:

* `@ [type] [flag] name [value]`

2.2 Examples:
* `@name;` — simple decorator
* `@!name;` — required decorator
* `@?name;` — optional decorator
* `@(type)name value` — typed decorator
* `@(type)!name value` — typed required decorator
* `@name("value1" 2 "value3")` — decorator with arguments

2.3 Notes:

* A decorator with a semicolon is equivalent to `true`


## 3. Properties

3.1 Syntax:

* `[type] [flag] name : [value]`

3.2 Examples:

* `trueProp: true`
* `(int)integer: 32`
* `listsProp: [ "one" "two" 3 and 4 ]` - returns: one, two, 3, and, 4
* `!requiredProp: ;` — empty but required

3.3 Notes:

* Properties are **key-value pairs**
* Properties have to have a value, which can be a **boolean**, **number**, **string**, **list**, or **empty**

## 4. Sections

4.1 Syntax:

* `[type] [flag] SectionName [flags]? { statements }`

4.1.1 `[flags]` Syntax:

* `[type] [flag] name {: value }?`
* Flags are meant to be used for configuration while keeping the data inside the node sterile

4.1.2 `[flags]` Examples:

* `flag`
* `(int)flag`
* `!requiredFlag`
* `?optionalFlag`
* `flag: 100`

4.2 Example:

```kavo
Section debug: true {
    cache: yes
    run() {
        return true
    }
}
```

4.3 Notes:

* Sections **group statements together**
* Can contain **properties, functions, decorators, macros, or nested sections**

## 5. Functions

5.1 Syntax:

* `[type] [flag] name ({param , }*)` `{` `arbitrary code` `}`

5.2 Notes:

* Functions are **data blocks**, not executed at compile time
* Can have optional flags: `!requiredFunction() { ... }`, `?optionalFunction() { ... }`
* Can contain anything

5.3 Example:

```kavo
coolFunc(arg) {
    if (arg == "hello") {
        return true
    }
}
```

```kavo
function() {
    console.log(`1+1 = ${1+1}, YAY Javascript`)
}
```

What actual language is being contained in the function is **up to you and the runtime**

However there is a way to pass the language to the function by appending the name of it between the args and the data block e.g.

```kavo
function() js {}
function() glsl {}
function() python {}
function() nuclearwarfarelang {}
function() anything {}
```

This only supports **one language per function**, having more than one will result in an error

## 6. Lists

6.1 Syntax:

* `[` ` [value] [value] ...` `]`

6.2 Example:

```kavo
numbers: [
    "100"
    "92" "Test"
    4
]
```


## 7. Macros

7.1 Syntax:

* `#name { \{ 'string' \} || value }` =>
* `#name { 'string' }`
* `#name value`
* Common macros: `#import`, `#merge`, `#validate`

7.2 Notes:

* Macros **do not produce runtime code**, but act as **compiler directives**
* `#validate` can enforce type checks and assert conditions

7.3 Common Macros

* `#import path` – imports a file and appends the children inside the file to the current section
* `#merge path` – imports a file and appends the children inside the file to the current section, while replacing same children
* `#validate { 'string' }` – adds a validation block

7.4 Validate:
* `section` is the current section in a table
* `root` is the document root, a.k.a the top-most layer
* `self` is the current node
* `section` is an object that has the property names and then the nodes as values
* `root` is a node, so it uses query like root.nav("section.property").value   

7.4.1 Example:

```kavo
#validate {
    if (!self.isExtended) return; // Ensures that only extended sections can be validated
    ensureType(section.prop)
}
```

## 8. Inheritance

8.1 Syntax:

* `[type] [flag] name extends otherName [flags]? { statements }`
    * `[flags]` see 4.1.1

8.2 Notes:

* Creates a **shadow node** for the `otherName` section
* Child can **override properties**
* Validation may use `self.isExtended`

8.2.1 Shadow Nodes:

> Shadow Nodes are invisible-ish nodes that don't carry data but reference, for example a file, which can then be used for post processing

8.3 Example:

```kavo
Rectangle {
    (int)!width: ;
    (int)!height: ;
}
CoolRectangle extends Rectangle {
    width: 10
    height: 10
}
```

## 9. Values & Types

9.1 Allowed types:

* Boolean: `true`, `false`
* Numbers: `1`, `1.0`, `-10`
* Strings: `"text"`, `no_quote_string`
* Lists: `[1 2 3]`
* Custom typed: `(int)`, `(str)`, `(rgba)`, `(vec3)`
* Empty: `;`

9.2 Types:

* str for strings
* int, number, float for numbers
* bool for booleans
* list, array for lists
* hex for 0x prefixed strings
* binary for 0b prefixed strings
* octal for 0o prefixed strings
* color for # prefixed strings
* rgb for rgb(x, y, z) or [x y z]
* rgba for rgba(x, y, z, a) or [x y z a]
* vec2 for [x y]
* vec3 for [x y z]
* vec4 for [x y z a]
* And any other type

9.3 Example:

```kavo
(color)color: '#ff00ff'
(binary)binaryNumber: '0b1010'
(hex)hexValue: '0x1A3'
(vec2)position2D: [100 200]
(vec3)position3D: [1 2 3]
(rgba)rgbaColor: [255 0 0 255]
```

## 10. Comments

10.1 Syntax:

* `{// | /*} comment {*/}?` =>
* `// comment`
* `/* comment */`

10.2 Notes:

* Comments are **ignored**

10.3 Example:

```kavo
// This is a comment
/* This is also a comment */
```

## 11. Whitespace

11.1 Syntax:
Whitespace is generally **ignored**, unless it is part of a string. It is often used as a **separator** between tokens and as indentation.

11.2 Usecases:

* Whitespace is used as a **separator** between tokens
* Whitespace is used as **indentation** to create a **hierarchical structure**

## 12. Newlines

In Kavo Newlines don't play a role, they are **ignored**. If you have Newlines inside a string they will be preserved

```kavo
section flag { prop: hey prop: dos }
```

and

```kavo
section flag {
    prop: hey
    prop: dos
}
```

are the same