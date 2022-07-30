---
layout: post
title: "Asynchronous"
date: 2022-07-28
categories: JavaScript
---

### Asynchronous 
what is asynchronous in javascript?
- In javascript there is the execution stack and the event cue, as soon as the execution task is empty, the event queue is entered

```javascript
function waitFourSecs(){
    var ms = 4000 + new Date().getTime();
    while(new Date() < ms ){}
    console.log('finished function');
}

function clickHandler(){
    console.log('click event!');

}

document.addEventListener('click',clickHandler);

waitFourSecs();
console.log('finished execution')
```

- The click even above will be executed last