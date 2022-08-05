---
layout: post
title: "Recap"
date: 2022-07-29
categories: General
---
### 
- `<a>  ` -  Renders clickable hyperlink
- `<ol> `
- `<ul> `
- `<li> `
- `<h1> ` - Through `<h6>`
- `<img>` - Renders pictures


### Forms
- `<input>` 
    - `type`
    - `label`
    - `id`
    - `submit`
    - `reset` clears the form data
    
### CSS

- Rulesets / rules
    - collections that specify elements to style and the styling to apply
- Declarations
    - property value pairs specifying the styling
- Selectors
    - determine which elements to apply the styling to
- Properties
    - kind of styling we are applying
- 
```css
p{
    background-color: green;
}
```
### Selectors
- id
    - prefix by #
- class
    - prefix by period
    - ```css
    .nameofclass{
}
    ```
- tag
    - write the name of the tag itself
- other attributes
- 
- combining multiple selectors
- ```css
p.nameofclass {

}
```

### where to include css

- inline
- externally
- 

### specificity
- Ruleset with the most specific selector takes precedence
- if one selects by `id` the other does not, the one with `id` takes precedence
- if there is a tie then we compare the n
- 
- 
### Box Model
- has four layers margin, border, padding, and content
- 
### sizing in hte css styles
- specify size in two ways:
    - absolutes
        - takes the same space of the window -  px cm in
    - relative
        - adapts to the size of the window in use % or em
### responsive
- implement styling
    - relative sizing in css declarations 

### Javascript
    
- loosely -typed
    - variables can be declared at run time
- dynamic
    - types 
- seven primitives
    - String
    - Number
    - BigInt
    - Null
    - Undefined
    - Symbol
    - boolean
- declarations    
    - var
        - older way prior to es6, 
        - global
            - outside function
        -  or function
            - inside function
    - const
        - for constants
        - enforces block scope
        - immutable
    - let
    - 
    - Hoisting
        - you can use var variables before assignment
        - 
    - Type coercion
        - implicit conversion of a type to another
        - 
### Control flow
- conditionals
    - if 
    - else
    - if else
- Ternary operator
    - short hand for ef else
    - `a = condition ? 'condition is true' : 'condition is false'; `

    - for of loop
        ```javascript
        for(let iterableVariable of iterableObject){
    
}
        ```
    - for in loop
    ```javascript
    for(let iterableVariable in Object){
}
    ```


### Arrays
- zero indexed
- use of square brackets
- ```javascript
let myArray = [1,2,3];

```
- dynamically sized in js
- .length
- initialize objects through object literals
- ```javascript
let myObject = {
    firstKey: 'first Value'
}
```
- refer to value using the dot notation `.` , or the square brackets
- 
- 
### Falsey Values
-    null
- undefined
- 0
- empty string
- NaN
- false
they evaluate to false in control flow

### functions
- 
### immediately invoked functions
```javascript
(function)(){}();

(()=>);

(()={
})();
```
### DOM
- Selector methods
- getElementById()
- getElementByTagName()
- getElementByClassName()
- querySelector()
    - uses css syntax
- querySelectorAll()
- 
### Event
- event listeners
    - attach to elements in the js code by using addEventListener(event, handler, useCapture)
    - event- event
    - handler - function to invoke
    - useCapture - determines if even fires in bubbling or capturing phases
    - to remove eventListener
### Event Propagation