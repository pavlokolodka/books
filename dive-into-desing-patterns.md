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
> Code reuse is one of the most common ways to reduce development costs (time and money).

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

### Program to an Interface, not an Implementation

> Program to an interface, not an implementation. Depend on abstractions, not on concrete classes.

This helps us to remove tight coupling between dependent class and the dependency. With the polymorphism mechanism the code becomes more flexible.

### Favor Composition Over Inheritance

> A subclass can’t reduce the interface of the superclass. You have to implement all abstract methods of the parent class even if you won’t be using them.

> When overriding methods you need to make sure that the new behavior is compatible with the base one. It’s important because objects of the subclass may be passed to any code that expects objects of the superclass and you don’t want that code to break.

> Inheritance breaks encapsulation of the superclass because the internal details of the parent class become available to the subclass. There might be an opposite situation where a programmer makes a superclass aware of some details of sub-classes for the sake of making further extension easier.

> Subclasses are tightly coupled to superclasses. Any change in a superclass may break the functionality of subclasses.

> Trying to reuse code through inheritance can lead to creating parallel inheritance hierarchies. Inheritance usually takes place in a single dimension. But whenever there are two or more dimensions, you have to create lots of class combinations, bloating the class hierarchy to a ridiculous size.

There’s an alternative to inheritance called **composition**. Whereas inheritance represents the **“is a”** relationship between classes (a car is a transport), composition represents the **“has a”** relationship (a car has an engine). his principle also applies to aggregation -  a more relaxed variant of composition where one object may have a reference to the other one but oesn’t manage its lifecycle.

## SOLID Principles

### Single Responsibility Principle

> A class should have just one reason to change.

Try to make every class responsible for a single part of the functionality provided by the software, and make that responsibility entirely encapsulated by (you can also say hidden within) the class.

---
### Open/Closed Principle

> Classes should be open for extension but closed for modification.

A class is **open** if you can extend it, produce a subclass and do whatever you want with it. A class is **closed** if its interface is clearly defined and won’t be changed in the future.

If you know that there’s a bug in the class, just go on and fix it; don’t create a subclass for it. *A child class shouldn’t be responsible for the parent’s issues*.

---
### Liskov Substitution Principle

> When extending a class, remember that you should be able to pass objects of the subclass in place of objects of the parent class without breaking the client code.

This means that the subclass should remain compatible with the behavior of the superclass. When overriding a method, extend the base behavior rather than replacing it with something else entirely.

List of the set of formal requirements for subclasses (specifically for their methods):

1. **Parameter types in a method of a subclass should match or be more abstract than parameter types in the method of the superclass.**

Example: Parent class method: `feed(Cat c)`.
- Bad: `feed(BengalCat c)`. Now method can accept only a specific type of cat, and wouldn't be work with parent class.
- Good: `feed(Animal c)`. A subclass is extending from accepting a cat to accepting all the animals (including the cat object). Now if you pass an object of this subclass instead of an object of the superclass to the client code, everything would still work fine.

2. **The return type in a method of a subclass should match or be a subtype of the return type in the method of the superclass.**

Reverse requirement to paramenter types (1)

Example: Parent class method: `buyCat(): Cat`.
- Bad: `buyCat(): BengalCat`. The client gets a Bengal cat, whichis still a cat, so everything is okay.
- Good: `buyCat(): Animal`. Now the client code breaks since it receives a generic animal that doesn’t fit a structure designed for a cat.

3. **A method in a subclass shouldn’t throw types of exceptions which the base method isn’t expected to throw.**

Types of exceptions should *match* or be *subtypes* of the ones that the base method is already able to throw.

`try-catch` blocks in the client code target specific types of exceptions which the base method is likely to throw. Therefore, an unexpected exception might slip through the defensive lines of the client code and crash the entire application.


4. **A subclass shouldn’t strengthen pre-conditions.**

If a method of base class accepts a parameter of type `int`, then if a subclass method accepts only a positive integers, this will cause an error. Default expectation of the client is not match for the subclass method.

5. **A subclass shouldn’t weaken post-conditions.**

If you have a method of the class is supposed to always close all opened database connections upon returning a value, and then created a subclass and changed it so that database connections remain open (for reuse purpose), client still thinking that it have closed a connecting through the subclass method. This will cause a polluting a system with ghost database connections.

6. **Invariants of a superclass must be preserved.**

Invariants are conditions in which an object make sense.

The rule on invariants is the easiest to violate because you might misunderstand or not realize all of the invariants of a complex class. Therefore, the safest way to extend a class is to introduce new fields and methods, and not mess with any existing members of the superclass.

7. **A subclass shouldn’t change values of private fields of the superclass.**

It turns out some programming languages let you access private members of a class via reflection mechanisms. Other languages (Python, JavaScript) don’t have any protection for the private members at all.

---
### Interface Segregation Principle

> Clients shouldn’t be forced to depend on methods they do not use.

Try to make your interfaces narrow enough that client classes don’t have to implement behaviors they don’t need. It's better to separate the interface to a standalone interfaces and use them where needed, rather than using one interface and implement behaviour that woun't be used. Otherwise, a change to a “fat” interface would break even clients that don’t use the changed methods.

---
### Dependency Inversion Principle

> High-level classes shouldn’t depend on low-level classes. Both should depend on abstractions. Abstractions shouldn’t depend on details. Details should depend on abstractions.

Usually in application there are two levels of classes:

- **Low-level classes** implement basic operations such as working
with a disk, transferring data over a network, connecting to a
database, etc.

- **High-level classes** contain complex business logic that directs
low-level classes to do something.

Algorithm of using Dependency Inversion Principle while designing a program:

1. Describe interfaces for low-level operations that high-level classes rely on, preferably in business terms.

2. Make high-level classes dependent on those interfaces, instead of on concrete low-level classes.

3. Once low-level classes implement these interfaces, they become dependent on the business logic level (interfaces), reversing the direction of the original dependency.


Example. Before Dependency Inversion:

```
+-----------------------------+
|     SomeService             |
+-----------------------------+
|   - database: MySqlDatabase |
+-----------------------------+
|   + get()                   |
|   + save()                  |
+-----------------------------+

          |
          |
          V

+----------------------+
|    MySqlDatabase     |
+----------------------+
|    + create()        |
|    + read()          |
|    + update()        |
|    + delete()        |
+----------------------+

```

After: High level class `SomeService` don't depend on `MySqlDatabase` class anymore.

```
+-----------------------+
|     SomeService       |
+-----------------------+
|  - database: Database |
+-----------------------+
|  + get()              |
|  + save()             |
+-----------------------+

          |
          |
          V

+----------------------+
| <interface> Database |
+----------------------+
|    + create()        |
|    + read()          |
|    + update()        |
|    + delete()        |
+----------------------+
        
          ^
          |
          |
        
+----------------------+
|    MySqlDatabase     |
+----------------------+
|    + create()        |
|    + read()          |
|    + update()        |
|    + delete()        |
+----------------------+

```

As a result, the direction of the original dependency has been inverted: low-level classes are now dependent on high-level abstractions.


# Catalog of design patterns