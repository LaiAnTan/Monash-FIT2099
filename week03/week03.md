# Week 03

## Static

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

## Final

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

## Encapsulation Boundary

An encapsulation boundary is simply something across which visibility can be restricted.

- Class
- Package
- Module
- Scope: `{}`

Any method call / attribute access that is not in the same class / package etc is crossing an encapsulation boundary.

These calls / accesses should be minimised.

### Packages

Classes in java can be grouped into packages.

A package should contain classes that are related.

### Modules

A module is a collection of Java packages.

In a module, there exists a module descriptor file (module-info.java) that specifies:

- name of the module
- which packages are public
- services that the module offers & consumes
- other classes that may apply reflection to packages in this module

for example:

```java
module my-module {
    requires javafx.controls; // dependency
    exports my.program.package; // make package visible
    exports my.program.package
        to other-module;  // make package visible to specific module
    provides someInterface 
        with my.program.Implementation;  // implements this interface
}
```

## Polymorphism

Polymorphism is the ability to define an interface / base and have multiple implementations.

## Abstract Class

Abstract classes are incomplete classes that are not meant to be instantiatied.

Rather, subclasses extend the abstract superclass and declare all abstract methods in the abstract class for it to be functional.

For example:

```java
public abstract class A {
    
    public abstract void method();
}

public class B extends A {
    
    @Override
    public void method() {
        System.out.println("Hello World!");
    }
}
```

In a UML class diagram, abstract class / method is defined as follows:

![abstract class](/assets/abstract_class.png)