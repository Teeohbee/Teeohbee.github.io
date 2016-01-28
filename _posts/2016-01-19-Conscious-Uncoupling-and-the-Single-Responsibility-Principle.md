---
layout: post
title: Conscious Uncoupling and the Single Responsibility Principle
---

> *A class should have only one reason to change* - Robert C. Martin, 2003

I've been reading a fair bit about the single responsibility principle recently, in refreshing my knowledge of Object Oriented Design and the SOLID design principles. In essence, the explanation of the single responsibility principle, henceforth referred to as SRP, is a simple one, it's in adhering to, and maintaining, the principle in your code that which things get tricky.

The simplest explanation is that in general every class, or module of code, should only ever have one 'job' - be responsible for only one aspect of functionality in the software.

Robert 'Uncle Bob' Martin's quote at the top of this blog post refers to one of the key advatnages that SRP classes afford you. Change. Change is inevitable. Requirements change, clients change, technologies change, everything changes and by following the SRP, you can somewhat mitigate the chaos that change usually causes in your codebase.

Let's look at a very simple code example using a good old fashioned game of battleship.

```Ruby
class Ship
  attr_reader :type, :size, :hp

  def initialize(type)
    @size = ship_types[type]
    @hp = size
  end

  def ship_types
    { patrol_boat: 2, destroyer: 3, submarine: 3, battleship: 4, aircraft_carrier: 5 }
  end

  def takes_a_hit
    @hp -= 1
  end

  def has_sunk?
    @hp == 0
  end
  
  def place_on_board()
    game_board = Board.new()
    game_board.add_ship
  end
end
```

So we've got a class called Ship, you instantiate it with an argument determining it's type and therefore size and health points. It has a method that allows it to take a hit, check to see whether it has sunk and place itself on a board. What looks wrong here?

There's a large code smell that indicates a problem in that we're instantiating a new Board class within our Ship class. This ship class's responsibility is to keep track of one item, a ship; is it the responsibility of a ship to actually create the board it is to be placed on?

There's nothing stopping you coding your project in this way, but this will be where problems start to seep into your program. Coupling is a term used in software engineering to describe the manner and extent of interdependence between software classes, and is generally regarded to not be a good thing. The more inter-dependencies you have between your classes, the more you'll have to change should any one single class change.

At the moment for example, our new board instantiation requires no additional arguments. A user somewhere down the line suggests that they'd like to choose the size of their board to affect the difficulty of play. The Board class is updated to take at least one argument and in the process breaks your implementation of the Ship class.

Sure it'd be a fairly simple change to update the ship class in the example, but in a real world project, things wouldn't be so easy. It pays dividends to think of these things now, when your classes are small, and your number of objects are limited. Basically do as Chris and Gwyneth did and try to consciously uncouple as many of your objects as possible.

Get rid of that method then, sure, but then how does a player place a ship on a board? Who's single responsibility is it to look after the actual playing of the Game?
