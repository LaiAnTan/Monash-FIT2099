# Week 02

## Association

An association between two objects implies that one object has the other object as an attribute.

For example:

```java
public class A {
    public B b;
}

public class B {}
```

Because class A has an object of type of class b as an attribute, class A has an association with (i.e. is aware of) class B.

![association](/assets/association.png)

## Dependency

A dependency relationship between two objects means that one object has used the object somewhere (method parameter, return type, in code etc).

For example:

```java
public class A {

    public void someMethod() {
        B b = new B(); // this is a dependency
        b.doSomething();
    }

    public B anotherMethod(B b) { // both of these signify dependencies
        b.doSomething();
        return b 
    }
}

public class B {
    public void doSomething() {
        // Some code here
    }
}
```

In UML, it is represented like this:

![dependency](/assets/dependency.png)

A dependency relationship between two classes is weaker than an association relationship between two classes.

> Note: An association relationship between two classes also means that there is a dependency relationship between two classes. (i.e. Association is a subset of Dependency)

## Multiplicity

Multiplicities are used to show the number of each class involved in a relationship.

> Note: The double dots `..` are read as 'or', and `*` is read as many.

For example:

![multiplcity](/assets/multiplicity.png)

Determining multiplicity from code:

```java
public class A {
    ArrayList<B> arr;
}

public class B {}
```

From the above code: we can see that A has an association relationship with B, where in 1 A, we can have 0 or more B (list):

![multiplicity in code](/assets/multiplicity_in_code.png)

## Other Association Subsets

There exist relationships which are subsets of association.
In particular, Aggregation and Composition.

![subsets of association](/assets/subsets_of_association.png)

### Aggregation

Aggregation is almost the same as association and is often redundant.

It refers to 

For example:

```java
public class A {
    private B b;
    
    A(B b) {
        this.b = b;
    }
}

public class B {}
```

In the code, A borrows B (from an external source). When A dies, i.e. goes out of scope, B lives on.

![aggregation](/assets/aggregation.png)

### Composition

Composition is a relationship that involves creational responsibility, where one object is responsible for the creation of another object.

For example:

```java
public class A {
    private B b = new B(); 
}

public class B {}
```

In the code, A created B, and owns B. When A dies, i.e. goes out of scope, B dies as well.

![composition](/assets/composition.png)

## Inheritance

## Design Principles
