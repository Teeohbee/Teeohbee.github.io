---
layout: post
title: Hoisting Duck In JavaScript
---

```javascript
var duck = "Donald";
console.log(duck);

function updateDuck(){
    console.log(duck);
    var duck = "Daffy";
    console.log(duck);
};

updateDuck();

console.log(duck);
```
