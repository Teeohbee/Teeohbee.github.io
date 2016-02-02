---
layout: post
title: Danger, Danger, Method Overload!
---

Coming to C# from Ruby, the concept of method overloading and how it worked was new to me, as it's not possible in Ruby. The reason for this is method overloading relies on C#'s strongly typed nature, and a facet of a method known as its signature.

## Method Signatures

A methods signature is used, much like a real signature, as a uniqueness indicator. It is not possible for a method to have the same signature as another. In the case of C#, a methods signature is defined by two parts of the method declaration itself, the name, and the parameters. It's worth noting that the return type of the method has no bearing on its signature at all.

```csharp
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

```csharp
int MethodOne(string inputstring)
  {
    // code here
  }
```

## Method Overloading

The importance of signatures become apparent when taking a closer look at the first codeblock again. We have two valid method definitions with the exact same name, `MethodOne`. This means one method can have multiple implementations based on the type or number of arguments being passed in as parameters.

This obviously opens up a lot of options. You can prepare a method to receive a number of different parameters and react accordingly based on the number of arguments it receives. You can execute completely different code based on what type of object is being passed in, customising the method even further. However, it's worth bearing in mind the end user experience when method overloading; as if overused it can increase complexity and decrease clarity when users aren't sure exactly how a method will react. Consider the example below.

```csharp
public List<Movie> GetAllMovies() {    // return a List of all movies    }
public List<Movie> GetMovieById(int movieId) {    // return a List by ID    }
public List<Movie> GetMovieByCategory(Category genre) {   // return a List by Category    }
public List<Movie> GetMovieByName(string searchString ) {   // return a List by search string    }

public List<Movie> GetMovies() {    // return a List of all movies    }
public List<Movie> GetMovies(int movieId) {    // return a List by ID    }
public List<Movie> GetMovies(Category genre) {    // return a List by Category   }
public List<Movie> GetMovies(string searchString ) {    // return a List by search string   }
```

Above we have two sets of methods, the first use explicit method names, while the second use method overloading. Each of the sets return the same results. Which set is more readable? Which one would make more sense to a newcomer reading your code? Is the `GetMovies` method intuitive enough for a user to know what will be returned when they pass something in, or that the method accepts arguments at all? These are all thing worth considering when deciding whether to use method overloading or not.
