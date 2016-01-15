---
layout: post
title: Reference Vs Value Types in C#
---

```csharp
int a = 3;
int b = 4;
a = b;
b += 6;
Console.WriteLine(a);
```

The code above is pretty self explanatory right? We're creating a variable `a` of type integer and assigning it a value of 3. then creating another integer variable, called `b`, and assigning it a value of 4. Two integer variables, all good so far. On line 3 we perform another assignment of `a = b`, then go on to add 6 onto whatever integer is stored in `b`. Finally, we print the value of `a` to the console, what do we expect to see?

You may be thinking I've lost my mind and the answer is obvious, and you'd be right, on one count at least. The answer is 3. Variable `b` now has a value of 10, but the original variable `a` is unchanged. What's the meaning of all this you ask?

Here's another example, this time using an object. Let's say we have a class called `NumberStore`, this class has a single property called `Number` that stores an integer. Let's got through similar steps to the above code.

```csharp
NumberStore a = new Numberstore();
a.Number = 3;
NumberStore b = new NumberStore();
b.Number = 4;

a = b
b.Number += 6;
Console.WriteLine(a.Number);
```

What would you expect to be displayed this time round? In fact, the answer is 9. Confused? Don't be - welcome to C#!

![_config.yml]({{ site.baseurl }}/images/helloworld.png)
