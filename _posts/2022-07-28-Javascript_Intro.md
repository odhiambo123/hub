---

layout: post
author: David

---

### Intro
- Javascript is an interpret language that web browsers can parse and execute.
- It is  single threaded ; meaning that JavaScript engines will run and execute code one process at a time.
- It is multi-paradigm ; meaning that it can be 
    - functional
    - object oriented
    - or procedural
- It is loosely typed and dynamically typed:
    - No need to declare type when declaring the variables
    - The variable types are declared at runtime.

### Data Types

- Number 
- String
- Boolean
- Undefined
- Symbol
- Null
- BigInt

### Variable Declarations

- `var` - hoisted
- `let` - not hoisted
- `const` - not hoisted
- 
### Hoisting


### Type Coercion

- Implicit conversion of the variable from one data type to another

|Value | Becomes...|
|______|___________|
|`Undefined`| `Nan`|
|`null`| 0 |
|`true`| 1 |
|`false`| 0 | 
|String | white space from the start and end of the string are removed. string with empty values are converted to 0. If possible, a string will be converted to number, else it will be converted to `NaN` |

- If one of the values is a String and the operator is `+`, the other value will be converted to a string as well.
- Using `==` to compare two entities? Javascript will try tio convert both to numbers.
- To check equality without type coercion, use the `===`


