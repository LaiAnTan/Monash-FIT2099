# Week 10

## Code / Design Smells

> A code smell is a surface indication that usually corresponds to a deeper problem in the system.
> -Martin Fowler

The "deeper problem" in the above context is usually a design problem.

Design smells are some bits of a design that indicate a broader problem.

### Smelly fixes

Fixes that make the system have ugly dependencies and harder to be extended.

### Common Code Smells

Martin Fowler devised a subjective, non definitive list of code smells:

![common_code_smells](/assets/common_code_smells.png)

### Code Length Smells

- Duplicated Code: DRY Principle
- Long Methods: Split into smaller methods
- Large Classes: Extract class / subclass
- Long Parameter Lists: Pass in an object instead

### Dependency Smells

#### Divergent Change

When there is a class that is repeatedly changed in a couple of different ways.

Signs point that there might be two distinct classes in that singular class.

Address divergent change by:

- Extracting class
- inheritance

#### Shotgun Surgery

Whenever a new feature is added, a lot of small changes must be added to many different classes.
If one place is missed, the code would not work.

Indicates possible poor encapsulation choices.

Address shotgun surgery by:

- Moving method / field into a single class
- Remove redundant classes

#### Feature Envy

A method in one class spends all its effort making multiple method calss to an object of a different class.

Indicates that it does not have the data it needs in the class where it currently is.

Address feature envy by:

- Moving method
- Extract method
- Move data to calling class

### Procedural Programming Smells

#### Primitive Obsession

Storing everything using primitive datatypes rather than using classes.

Address primitive obsession by:

- Group using class

#### Data Clumps

Groups of variables that pop up repeatedly all over code to represent the same information

Address data clumps by:

- Group using class

#### Too many same conditionals

Same cascade of switch statements / if else trees in multiple places.

Extensibility is hard because all of them have to be changed.

Address this by:

- Extract conditional trees into class / method
- Polymorphism

#### Data Classes

Classes that have no logic in them, (like structs in C / C++).

A smell in **OOP design** only.

Address data classes by:

- Encapsulating attributes if they are public
- Extract the code from the method that uses the data and put it in the data class

#### Message Chains

When a client request an object, and said object requests another object, and that object requests another object and so on.

This means that the client is dependent on navigation along the class structure.

Address message chains by:

- Reducing delegates
- Move or extract methods to the beginning of the chain

#### Middle Man

Class that does one one thing, which is delegating work to another class.

It does not have to exist for the system to function.

Address middle man by:

- Removing middle man class and calling method directly

### Overengineering

#### Speculative Generality

When a bunch of functionality is added to make a class extensible for every special case, especially if it is never used.

#### Lazy Class

A class that does not play a significant role in the system any more, after refactorings have been done.

### Refactoring

> Refactoring is a disciplined technique for restructuring an existing body of code, altering its internal structure without changing its external behavior.
> -Martin Fowler

#### Benefits of refactoring

- improves design of the system (more extensible)
- improves understandability of code
- easier debugging

### When to refactor

![when_to_refactor](/assets/when_to_refactor.png)

Possible situations to refactor:

- adding new features
- fixing a bug
- code review

### Metatechnique for Refactoring

1. make small change that eliminates / reduces code smell
2. test
3. repeat until code smell not evident
