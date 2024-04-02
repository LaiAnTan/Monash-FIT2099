# Week 01

## Object-oriented Design

To **"design"** a software is to make decisions about how the software is implemented such that:

- It has one functionality
- It is maintainable and extensible

## Abstraction

```java
abstract class Ball1 {
    public String brand;
    public String color;
}

abstract class Ball2 {
    public double radius;
    public int[] someArray = new int[2];
}
```

## Seperation of Concerns

> It is what I sometimes have called "the separation of concerns", which, even if not perfectly possible, is yet the only available technique for effective ordering of one's thoughts, that I know of. This is what I mean by **"focusing one's attention upon some aspect"**: it does not mean ignoring the other aspects, it is just doing justice to the fact that from this aspect's point of view, the other is irrelevant.
>  
> **It is being one- and multiple-track minded simultaneously.**
>
> E.W Dijkstra, "On the Role of Scientific Thought"

In programming, a **"concern"** is a responsibility.

Basically, the seperation of concerns state that:

- Every module should have a single & well-defined set of responsibilities (i.e. each module addresses a "concern" in the software)
- Responsibilities should overlap as little as possible with other modules

This can be achieved by means of abstraction and encapsulation.

A program that embodies the Seperation of Concerns well is called a _modular_ program.

## Encapsulation

> Encapsulation is the **grouping of ideas into one unit, which can thereafter be referred to by a single name**.
>  
> Object-oriented encapsulation is the packaging of operations and attributes representing state into an object type so that state is accessible or modifiable only via the interface provided by the encapsulation.
>  
> Meilir Page-Jones, Fundamentals of Object-Oriented Design in UML

