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

The first few lines of code should be fairly straight forward. We instantiate a NumberStore object with the `new NumberStore()` command and then set that objects `Number` property to 3. We then go through the process again for a new instance of the NumberStore class, this time giving its property Number the value of 4.

Line 6 is the key here. On this line it looks like we simply assign the value of `a` to the variable `b`, but that isn't strictly true. It comes down to the way variables are stored or referenced in C# depending on their type, and in this case, as the blog title suggests, we've got examples of a value and reference type variable.

###Value Types
Value types are the simpler of the two and demonstrated in the first example above. The reassignment of variable `a` to the value of `b` is exactly that, the variable changes from storing the integer 3 to the integer 4. These integers are static values, and thus after assigning `a` to `b`, changing the value of one variable doesn't affect the other.

###Reference Types
Reference types at first appear to display odd beahviour, especially in the example above, until you understand exactly how they work. Rather than storing a value, the NumberStore variables in the example simply contain a reference to that object's location on the heap. When a new object is instantiated with `new NumberStore`, that object is created and stored somewhere in memory, any variable created to hold that object simply points to that specific point in memory.

So on the crucial line 6, we are not assigning the value of `b` to `a`, we're actually changing the variable `a` to actually point to NumberStore `b`'s location in memory. After this point in the code, both variable `a` and `b` are pointing to the exact same object in memory, and so it follows that any change to one variable, will affect the other. It's also worth noting that at this point the original NumberStore object assigned to variable `a` has been lost, cannot be reached, and will eventually be cleaned up by the system and removed.
