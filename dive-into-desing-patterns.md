![Book](https://refactoring.guru/images/patterns/book/web-cover-en.png)

# Introduction to OOP
## Pillars of OOP

> Abstraction is a model of a real-world object or phenomenon,
limited to a specific context, which represents all details relevant to this context with high accuracy and omits all the rest.

> Encapsulation is the ability of an object to hide parts of its state and behaviors from others objects, exposing only a limeted interface to the rest of the program.

In context of the OOP encapsulate means to make something *private*, or less restrictive using *protected*.

Interfaces and abstract classes/methods built on concept of abstraction and encapsulation. Interface mechanism allows you define contract of interaction between objects.

> Inheritance is the ability to build new classes on top of existing ones. The main benefit of inheritance is code reuse. 

> Polymorphism is the ability of a program to detect the real class
of an object and call its implementation even when its real
type is unknown in the current context.

## Relations Between Objects
> Association is a type of relationship in which one object uses or
interacts with another. In UML diagrams the association relationship is shown by a simple arrow drawn from an object and
pointing to the object it uses. By the way, having a bi-directional association is a completely normal thing. In this case,
the arrow has a point at each end.

> Dependency is a weaker variant of association that usually
implies that there’s no permanent link between objects.
Dependency typically (but not always) implies that an object
accepts another object as a method parameter, instantiates, or
uses another object. Here’s how you can spot a dependency
between classes: a dependency exists between two classes if
changes to the definition of one class result in modifications
in another class.

> Composition is a “whole-part” relationship between two
objects, one of which is composed of one or more instances of
the other. The distinction between this relation and others is
that the component can only exist as a part of the container.
In UML the composition relationship is shown by a line with
a filled diamond at the container end and an arrow at the end
pointing toward the component.

> Aggregation is a less strict variant of composition, where one
object merely contains a reference to another. The container doesn’t control the life cycle of the component. The component can exist without the container and can be linked to
several containers at the same time. In UML the aggregation
relationship is drawn the same as for composition, but with an
empty diamond at the arrow’s base.

# Introduction to desing patterns

> Design patterns are typical solutions to commonly occurring
problems in software design. They are like pre-made blueprints that you can customize to solve a recurring design problem in your code.

The pattern is not a specific piece of code, but a general concept
for solving a particular problem. You can follow the pattern
details and implement a solution that suits the realities of your
own program.

## Classification

The most basic and low-level patterns are often called **idioms**. 
They usually apply only to a single programming language. <br/>
The most universal and high-level patterns are **architectural patterns**. Developers can implement these patterns in virtually any language. Unlike other patterns, they can be used to
design the architecture of an entire application. <br/>

In addition, all patterns can be categorized by their intent:
* Creational patterns provide object creation mechanisms that increase flexibility and reuse of existing code.
* Structural patterns explain how to assemble objects and classes into larger structures, while keeping the structures flexible
and efficient.
* Behavioral patterns take care of effective communication and the assignment of responsibilities between objects

## Motivation
1. Patterns are already tried and tested solutions to common problems in software design. So whether you've already encountered a common problem or not, it's good to know that there's a ready-made solution and you don't have to reinvent the wheel. 
2. Desing patterns are the key to understanding. Regardless of the language, you can communicate more effectively (you don't have to explain your idea) if you and the other developer know the pattern.

# Software design principles

# Catalog of design patterns