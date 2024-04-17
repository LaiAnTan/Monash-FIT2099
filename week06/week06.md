# Week 06

## Defensive Copying

Defensive Copying is the act of a getter returning a reference to a private object that is mutable.

Defensive Copying is used to ensure that modifications to an object do not affect the original object.

```java
Point p1 = new Point(3, 2);
Point p2 = new Point(p1); // same coordinates as p1, but different object (p1 is copied)
```

### Privacy Leak

A privacy leak is when getters return a reference to a private object that is mutable, and that object is mutated outside of the class. This breaks encapsulation as the state of the object can be changed directly without going through methods of the class.

Consider the following code:

```java
public class MutableClass {
    private List<String> items;

    public MutableClass() {
        this.items = new ArrayList<>();
    }

    public List<String> getItems() {
        return items; // Privacy leak here
    }
}

// somewhere else...
MutableClass mutable = new MutableClass();
List<String> items = mutable.getItems();
items.add("new item"); // This modifies the internal state of the mutable object, which is not allowed.
```

Instead, defensive copying is used to stop privacy leaks.

```java
public class MutableClass {
    private List<String> items;

    public MutableClass() {
        this.items = new ArrayList<>();
    }

    public List<String> getItems() {
        return new ArrayList<>(items); // defensive copy
    }
}

// somewhere else...
MutableClass mutable = new MutableClass();
List<String> items = mutable.getItems();
items.add("new item"); // This modifies a different object, not the original
```

> Note: other classes that are private also need to be defensively copied when returned (copy constructor)

## Dependency Injection

Dependency injection is a design pattern that aims to decouple objects from their dependencies.

Without dependency injection

```java
class Car {
    private final Engine engine = new Engine();
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void start() {
        engine.start();
    }
}
```

In the code snippet above, the Engine dependency is constructed by the class Carhhitself.

With dependency injection:

```java
class Car {
    private final Engine engine;
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void start() {
        engine.start();
    }
}
```

With dependency injection, the Car class gets the Engine dependency from an external source.

Therefore, a high-level module does not need to know anything about the low-level module its using.

### Benefits of Dependency Injection

- reusability of code
- easy to test / refactor

### Terminology

- client: class that is using the service
- service: dependency that is injected into the client
- interface: abstract interface that defines the methods that can be called in the serivce
- **injector**: external module that gives the serivce to the client

### Types of Dependency Injection

There are 3 main types of dependency injection:

a) Constructor injection: An instance of the service is passed into the client's consturctor

```java
class Car {
    private final Engine engine;
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void start() {
        engine.start();
    }
}
```

b) Setter injection: The client has a concrete setter that the injector can use to pass in the service instance

- requires a public setter, may be bad for information hiding

```java
class Car {
    private final Engine engine;

    public Car() {}

    public void setEngine(Engine engine) {
        this.engine = engine;
    }

    public void start() {
        engine.start();
    }
}
```

c) Interface injection: the client implements an interface that allows the injector to pass in the service instance

- increase complexity as dependencies increase
- explicity define dependency contract

```java
interface InjectEngine {
    public void injectEngine(Engine engine);
}

class Car implements InjectEngine {
    private final Engine engine;

    public Car() {}

    public void injectEngine(Engine engine) {
        this.engine = engine;
    }

    public void start() {
        engine.start();
    }
}
```

d) Method injection: similar to setter injection, but can be used in any method

### Testing with Dependency Injection

We can test the main service by replacing the dependencies with **mocks**.

Mocks are stub classes that pretend to provide the service, but they only provide preprogrammed responses.

### Dependency Injection Frameworks

There exist many software packages that do dependency injection.

Typically, the package supplies the injector, and also manage other aspect of the system, for example:

- persistence (database interaction)
- REST API binding
- connection to web frameworks

For example:

- Spring
- Guice
