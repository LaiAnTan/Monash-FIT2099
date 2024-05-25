# Week 09

## Design

A good software design leads to a successful product.

### Characteristics of Good Software Design

#### Simplicity

The amount and type of software elements needed to solve a problem.

#### Coupling

A measure of **interdependence** between two or more modules (eg. classes).

- No dependencies between modules -> Uncoupled
- Some dependencies between modules -> Loosely coupled
- Many dependencies between modules -> Highly coupled

#### Cohesion

The degree to which a software module (e.g. class) is strongly related and focused in its responsibilities.

> Coupling - interdependencies between modules  
> Cohesion - how related the functions within a single module are

#### Information Hiding

A component encapsulates its behaviors and data, hiding the implementation details from other components.

#### Performance

The analysis of an algorithm to determine its performance in terms of time (i.e. speed) and space (i.e. memory usage).

#### Security

A set of technical controls intended to protect and defend information and information systems.

### Dependency Control

Dependency Control is one of the key principles of good software design.

Dependency Control aims to solve the biggest issue in design:

>controlling the extent and nature of dependencines

Applying dependency control, dependencies are:

- only present when necessary
- explicit
- easy to understand

#### Direct Dependencies

Classes directly depend on one another.

#### Inverted Dependencies

Low-level modules and high-level modules both depend on abstractions (i.e. abstract class / interfaces)

## Connascence

Connascence is about the way elements in OOP design depend on each other.

Described by Meilir Page-Joens in the early 1990s, based on earlier ideas of cohesion and coupling.

> More explicitly, I define two software elements A and B to be connascent if **there is at least one change that could be made to A that would necessitate a change to B in order to preserve overall correctness.**

Connasence is used to reason about the complexity caused by dependency relationships in OOP design.
A higher level of connasence means that it is more complex.

### Types of Connascence

a) Static Connascence

- Obvious from code structure
- Easily identifiable by IDE / Analysis Tools

b) Dynamic Connascence

- Only obvious upon close inspection / execution
- Not easily identifiable by IDE
- More concerning in general

### Levels of Connascence

![levels_of_connascence](/assets/levels_of_connascence.png)

### Connasence of Name (CoN)

When two or more components must agree on the name of an entity.

If the name of a method changes, callers of that method must be changed to use the new name.

```java
public class Main {

    public String getTitles() { // here
        String titles = "";
        return titles;
    }

    public static void main(String[] args) {
        System.out.println("Titles: " + getTitles()); // if getTitles changes name, we have to change it here as well
    }
}
```

### Connasence of Type (CoT)

When two or more components must agree on the type of an entity.

If the name of an entity changes, callers of that method must be changed to adapt to the new type.

```java
public class Main {

    public int rentalDaysSince(Date date) {
        int numberOfDays = 0; // here
        // logic here
        return numberOfDays;
    }

    public static void main(String[] args) {
        Date date = new GregorianCalander(2014, Calender.FEBRUARY, 11).getTime();
        int rentalDays = rentalDaysSince(date); // if rentalDaysSince changes datatype, we have to adapt here
        System.out.println("Rental days: " + rentalDays); 
    }
}
```

### Connasence of Meaning (CoM)

When the interpretation of data in two elements must be identical.

i.e. what do magic numbers, magic strings, null / None, booleans mean in the current context.

```c
// C code
int isEven(int a) 
{
    // in this case, 1 means the number is even, 0 means the number is not even.
    if a % 2 == 0
    {
        return 1
    }
    else
    {
        return 0
    }
}

int main()
{
    int a = 3;
    printf("%d is even? : %d", a, isEven(a));
}

```

### Connasence of Position (CoP)

When the location / position of an entity matters.

For example, the position of arguments in a method's signature.

```java
public class Client {

    public void saveClient(String firstName, String lastName, String address) {
        // logic
    }

}

public class Main {

    public static void main(String[] args) {
        Client client = new Client();
        client.saveClient("Micheal", "Doe", "Melbourne"); // the position of these arguments matter
    }

}
```

### Connasence of Algorithm (CoA)

When two components must agree on a particular algorithm in order to work correctly.

For example, encryption systems mus agree on a particular algorithm. (SHA-2, SHA512 ...)

### Connasence of Execution (CoE)

When the order of execution of components is important.

i.e. things need to be executed in a particular order for it to work.

```python
# python code

email = Email()
email.setReciepient("test@gmail.com")
email.send()
email.setSubject("Hello World") # this is in the wrong order, it will not work
```

### Connasence of Timing (CoT)

When the timing of execution of components is important.

Usually happens in:

- parallel computing
- software-hardware interaction

### Connasence of Value (CoV)

When several values must change together.

### Connasence of Identity (CoI)

When multiple components **reference** the same entity. (Not copies of the same object)
