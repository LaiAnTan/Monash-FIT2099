# Week 01

## Object-oriented Design

To **"design"** a software is to make decisions about how the software is implemented such that:

- It has one functionality
- It is maintainable and extensible

## Abstraction

To abstract in software design means to decide:

a) what information to represent some item / concept

b) what to expose to the rest of the code, i.e. make `public`

---

To answer a), we decide what information we need to represent some item / concept based on how to information will be used.

Consider two Ball abstract classes:

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

The two classes will have different use cases in different software, so they have different fields.

Abstraction just means to show only essential details to the user of the method / class / package.

Simply, abstraction is performed by:

- colecting lines of code into methods / functions
- collecting data into classes
- grouping classes into packages

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

The defenition of Encapsulation:

> Encapsulation is the **grouping of ideas into one unit, which can thereafter be referred to by a single name**.
>  
> Object-oriented encapsulation is the packaging of operations and attributes representing state into an object type so that state is accessible or modifiable only via the interface provided by the encapsulation.
>  
> Meilir Page-Jones, Fundamentals of Object-Oriented Design in UML

To encapsulate is to group attributes and methods into a class.

## Information Hiding

The defenition of Information Hiding:

> Information/implementation hiding is **the use of encapsulation to restrict from external visibility certain information or implementation decisions** that are internal to the encapsulation structure.
>  
> Meilir Page-Jones, Fundamentals of Object-Oriented Design in UML

Put simply, information is hidden (restricted external visibility) through the means of encapsulation (the packaging of operations so that it is only accessible via the interface provided).

This makes the code simpler from the outside, as the internal implementation should not have to be considered.

In Java, **access modifiers** can be used for information hiding.

- `public` means that the field / method is visible outside the class.
- `private` means that the field / method is only visible inside the class.
- `protected` means that the field / method is only visible inside the class and its child classes.

Respecting encapsulation, we can use a combination of the `private` access modifier and the concept of `getter` and `setter` to hide information.

```java
class Balance {
    private double amount;

    public double getAmount() {
        return this.amount;
    }

    public void setAmount(double amount) {
        this.amount = amount;
    }
}
```

## Abstraction vs Encapsulation vs Information Hiding

Abstraction - deciding which things should be grouped

Encapsulation - grouping things together

Information Hiding - to hide implementation details / informations from external sources through encapsulation

## Class Diagram

A class diagram is a standard way to visualise the design of a system.

It is usually drawn in the language of **UML (Unified Modelling Language)**, which is a general-purpose, developmental, modelling language.

A class in a UML class diagram looks like this:

![alt text](/assets/class.png)

> Note about access modifiers:
>  
> - `public`: +
> - `private`: -
> - `protected`: #
>  
