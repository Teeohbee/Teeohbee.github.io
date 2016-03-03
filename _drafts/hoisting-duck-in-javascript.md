---
layout: post
title: Hoisting Duck In JavaScript
---

Terrrible pun in the title I know, but bear with me on this one.

Hoisting and Scope in javascript are popular subjects for discussion, and blog posts, as they represent some of the quirks of working in one of the webs most popular languages. They also make great topics for technical interview questions, something I found out to my horror when I got tripped up by just such a question at interview last year.

I fumbled my way through a bodged explanation while I desperately tried to logically work through the example I was being shown. Needless to say, I didn't get the job, but I did go back and research the issue, wanting to get a firmer grip on my understanding of scope and hoisting.

The question involved being shown a snippet of code similar to that below, except with less ducks. I was tasked with estimating exactly what each of the console.logs would display.

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

Now an awful person, who's terrible at coding might suggest `Donald`,`Donald`,`Daffy`,`Daffy`. They would of course be very wrong. Don't be that guy, especially at interview.

```javascript
var duck = "Donald";
console.log(duck);      //=>  "Donald"

function updateDuck(){
    console.log(duck);  //=>  undefined
    var duck = "Daffy";
    console.log(duck);  //=>  "Daffy"
};

updateDuck();

console.log(duck);      //=> "Donald"
```
