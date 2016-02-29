---
layout: post
title: Hoisting Duck In JavaScript
---

```javascript
var name = "Donald";
console.log(name);

duck();

function duck(){
    console.log(name);
    var name = "Daffy";
    console.log(name);
};

duck();

console.log(name);
```
