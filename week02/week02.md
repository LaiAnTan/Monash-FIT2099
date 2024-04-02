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

Inheritance is a relationship between two classes where one class acquires the 'properties' of another class.

The superclass (parent class) is the class being inherited from.
The subclass (child class) is the class that inherits from a superclass.

In UML, Inhertiance is also known as Generalisation, where one class extends another class.

Consider the code below:

```java
public class A {
    public final String name = "name";
    private int number;
    protected boolean isTrue;
    
    // other members...
}

public class B extends A {

    public String foo;

    public B(String foo) {
        super(A); // call constructor of superclass
        this.foo = foo;
    }

    public void someMethod() {

        String n = super.name; // accessing public attribute of superclass using super keyword
        boolean y = this.isTrue; // access protected attribute of subclass

        // note: we cannot access private attributes of superclass in subclass
    }
}
```

The Child class extends (inherits) from the Parent class.

The code also shows the ways to access different attributes involving inheritance, and also calls the constructor of the superclass.

![inheritance](/assets/inheritance.png)

### Static

The static keyword states that an attribute or method belongs to the class itself rather than instances of the class.

Consider the code below:

```java

class A {
    public static int someValue = 5;

    public static int getSomeValue() {
        return A.someValue;
    }
}

// somewhere else...

int a = A.someValue // 5
int b = A.getSomeValue() // 5
```

someValue and getSomeValue are static attribute and method respectively, and can be accessed from anywhere using prefix of class name A.

### Method overriding

Overriding allows a subclass to have a different implementation of a method in the superclass.

For example:

```java
class A {

    protected String method() {
        return "Foo";
    }
}

class B extends A {

    @Override // optional for readability
    public String method() { // we can change the access modifier from protected to public, but not protected to private
        return "Bar"; // overriden, different implementation
    }
}

```

### Final

The final keyword means that the current attribute / method / class, it means that it cannot be overridden in the future, and the current implementation is the final implementation (i.e. constant).

final in Java is similar to const in other languages

Consider the code:

```java
class A {

    public final int foo = 1;

    A() {
        this.foo = 2; // error, cannot reasssign final attribute
    }

    final int getFoo() {
        return this.foo;
    }

}

final class B extends A {

    @Override
    int getFoo() { // error, cannot override final method
        return 2;
    }

}

class C extends B {} // error, cannot extend final class
```

## Design Principles

### Don't Repeat Yourself (DRY)

A principle of software development aimed at reducing repetition of software patterns.

### Classes should be responsible for their own properties

A basic rule such that if things change at the same time, you should keep them in the same place.

### Avoid excessive use of literals

Do not use too many fixed values in code.
