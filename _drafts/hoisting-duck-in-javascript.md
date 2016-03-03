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

updateDuck();

function updateDuck(){
    console.log(duck);
    var duck = "Daffy";
    console.log(duck);
};

console.log(duck);
```

Now an awful person, who's terrible at coding might suggest `Donald`,`Daffy`,`Daffy`. They would of course be very wrong. Don't be that guy, especially at interview :cry:.

```javascript
var duck = "Donald";

updateDuck();

function updateDuck(){
    console.log(duck);  //=>  undefined
    var duck = "Daffy";
    console.log(duck);  //=>  "Daffy"
};

console.log(duck);      //=> "Donald"
```
The first thing of note here is that updateDuck() is able to run despite the named function being decalred further down the page. This is because of hoisting, a process in by which at runtime, javascript scans your code and moves any function declarations to the top of the page, therefore making them immediately available to invoke as seen in the example above.

Hoisting doesn't just move functions however, as can be seen within the code of our updateDuck function. The first console.log returns `undefined`, this may trip you up for several reasons. Firstly, you'll notice that we're defining a brand new variable of duck within the scope of our function, we are not updating the parent variable duck at all in this function. Fair enough then, at the point in time of the first console.log, the new variable hasn't been defined, but shouldn't `duck` at this point in time reference the parent variable? Why doesn't this return `Donald`?

This is because, variable declarations are hoisted too, in much the same was as functions. Once javascript hoisting has taken place, function and variable declarations have been moved to the top, you'll more clearly be able to see what is going on.

```javascript
var duck = "Donald";

function updateDuck(){
    var duck;
    console.log(duck);  //=>  undefined
    duck = "Daffy";
    console.log(duck);  //=>  "Daffy"
};

updateDuck();

console.log(duck);      //=> "Donald"
```

This is what javascript 'sees' and runs and it's clear now why that initial duck variable is undefined, it's been declared, scoped to that particular function and thus no longer linked to the parent variable of the same name. Yet it hasn't been assigned to anything.

It's also important to note that we declared and assigned a second variable called duck, only within the scope of that particular function. There's nothing in that function that will change the parent classes variable of the same name. This is clear when we see that the final console log displays `Donald`, returning the first variable we declared at the top of the code.

Working through this, and specifically playing around in a basic JS file and the chrome console really helped me to understand exactly what was happening here, and I'm hoping I'll be able to explain it a bit better if I ever encounter a similar question again.

Hoisin Duck, Hoisting Duck, do you get it?
