# Week 04

## Enumeration

Enums are a special type of class that contain constant values.

```java
public enum Days {
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    // and so on...
}
```

Enums are used to represent values that stay the same throught the runtime of code.

Enums can reduce the use of magic numbers in code, making it easier to maintain / extend it in the future.

![enum](/assets/enum.png)

## Interfaces

An interface is just a fully abstract classs that is used to group related abstract methods.

It is usually described as a 'blueprint' of what a class must do.

Interfaces can also contain default (defender / virtual extension) methods.

Default methods are commonly used to incrementally provide additional functionality to a given type without breaking down the implementing classes (i.e. no need to add implementation to all implementing classes, it will just use the default).

Syntax:

```java
interface A {
    public void method();
    public void anotherMethod();
    default void defaultMethod() { // default method
        System.out.println("Default");
    }
}

class B implements A {

    public void method() {
        // some implementation...
    }

    public void anotherMethod(); {
        // more implementation...
    }
}
```

![interface](/assets/interface.png)

### Benefits of Interfaces

Interfaces are used to achieve abstraction and loose coupling.

It allows programmers to seperate the definition of a method from the inheritance hirearchy.
