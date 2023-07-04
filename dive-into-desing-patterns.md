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

## Features of good design
### Code reuse
> Code reuse is one of the most common ways to reduce devel-
opment costs (time and money).

Tight coupling between components, dependencies on concrete classes instead of interfaces, hardcoded operations — all of this reduces flexibility of the code and makes it harder to
reuse it. 

Using design patterns is one way to increase flexibility of software components and make them easier to reuse. The trade-off of it - is the price of complicating the software components.

### Extensibility

> Change is the only constant thing in a programmer’s life.

Once you have started solving a problem, you can better understand it. That's why you'd rather rewrite the entire application from scratch than redesign it.

It's crucial to provide for possible future changes when designing an application’s architecture.

## Design Principles

Design principles are different depending on the type of application you’re building. Nevertheless, there are several universal principles of soft-
ware design that serves as the foundation for most of desing patterns.

You can tell that the design is flexible enough if you can easily extend it without breaking any existing code.
## Encapsulate What Varies

> Identify the aspects of your application that vary and separate them from what stays the same.

### Encapsulation on a method level

If some peace of code can vary in a function, it's better to remove it to the separate function. By doing this, you provide a stable interface and if you need to change something, it can be done in one place.

```
// Before
method getOrderTotal(order) is
    total = 0
    foreach item in order.lineItems

    total += item.price * item.quantity

    if (order.country == "US")
        total += total * 0.07 // US sales tax
    else if (order.country == "EU"):
        total += total * 0.20 // European VAT
    return total

// After
method getOrderTotal(order) is
    total = 0
    foreach item in order.lineItems
        total += item.price * item.quantity

    total += total * getTaxRate(order.country)

    return total

method getTaxRate(country) is
    if (country == "US")
        return 0.07 // US sales tax
    else if (country == "EU")
        return 0.20 // European VAT
    else
        return 0
```
### Encapsulation on a class level

Similar thing comes to classes. As you add more and more logic to your class, it can blur the main purpose of it. Extracting everything that can be done separately to a new class might make things much more clear and simple.

## Program to an Interface, not an Implementation

> Program to an interface, not an implementation. Depend on abstractions, not on concrete classes.

This helps us to remove tight coupling between dependent class and the dependency. With the polymorphism mechanism the code becomes more flexible.

# Catalog of design patterns