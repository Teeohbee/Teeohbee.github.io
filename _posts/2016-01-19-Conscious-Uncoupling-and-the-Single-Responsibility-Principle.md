---
layout: post
title: Conscious Uncoupling and the Single Responsibility Principle
---

> *A class should have only one reason to change* - Robert C. Martin, 2003

I've been reading a fair bit about the single responsibility principle recently, in refreshing my knowledge of Object Oriented Design and the SOLID design principles. In essence, the explanation of the single responsibility principle, henceforth referred to as SRP, is a simple one, it's in adhering to, and maintaining, the principle in your code that which things get tricky.

The simplest explanation is that in general every class, or module of code, should only ever have one 'job' - be responsible for only one aspect of functionality in the software.

Robert 'Uncle Bob' Martin's quote at the top of this blog post refers to one of the key advatnages that SRP classes afford you. Change. Change is inevitable. Requirements change, clients change, technologies change, everything changes and by following the SRP, you can somewhat mitigate the chaos that change usually causes in your codebase.

Let's look at a very simple code example using a good old fashioned chess analogy.

```Ruby
class Pawn
  def initialize(xaxis, yaxis)
    @xaxis = xaxis
    @yaxis = yaxis
  end
  
  def place_on_board
    board = Board.new(10, colour)
    board.accept_piece
  end
end
```
