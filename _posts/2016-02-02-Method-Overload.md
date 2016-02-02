---
layout: post
title: Hello World
---

Coming to C# from Ruby, the concept of method overloading and how it worked was new to me, as it's not possible in Ruby. The reason for this is method overloading relies on C#'s strongly typed nature, and a facet of a method known as its signature.

## Method Signatures

A methods signature is used, much like a real signature, as a uniqueness indicator. It is not possible for a method to have the same signature as another. In the case of C#, a methods signature is defined by two parts of the method declaration itself, the name, and the parameters. It's worth noting that the return type of the method has no bearing on its signature at all.

```CSharp
string MethodOne(string inputstring)
  {
    // code here
  }
  
string MethodTwo(string inputstring)
  {
    // code here
  }

string MethodOne(string inputstring, int inputnumber)
  {
    // code here
  }
```

In the code above, we define an example method of `MethodOne` that takes one argument, a `string` called `inputstring`. The method below takes the same parameter as the first method, but has an entirely different name, so of course the signature will be different to that of the first method.

The final method however, uses the same name - `MethodOne` - but instead requires different input, and so will also have a different signature to the initial method declared.

Also note that simply changing the return type, will not change the methods signature, the code below would be invalid as it would have the same signature as the original `MethodOne`.

```CSharp
int MethodOne(string inputstring)
  {
    // code here
  }
```
