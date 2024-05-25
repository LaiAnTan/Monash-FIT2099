# Week 11

## Refactoring

> Refactoring is a disciplined technique for restructuring an existing body of code, altering its internal structure without changing its external behavior.
> -Martin Fowler

Refactoring is a possible response to resolve code smells after identifying them, or for maintaining extensibility of code when new features are required.

### Benefits of refactoring

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

## Factory Pattern

A factory pattern is a design pattern that provides an interface for creating objects but allows subclasses to decide which class to instantiate, without specifying their concrete classes.

Suppose we have different shapes, as structured below:

```java

public interface Shape {
    void whatAmI();
}

public class Rectangle implements Shape {

   @Override
   public void whatAmI() {
      System.out.println("Rectangle");
   }
}

public class Square implements Shape {

   @Override
   public void draw() {
      System.out.println("Square");
   }
}

public class Circle implements Shape {

   @Override
   public void whatAmI() {
      System.out.println("Circle");
   }
}

```

If we wanted to instantiate different shapes without calling their constructors, we would use a factory pattern as such:

```java
public class ShapeFactory {

    public Shape getShape(String shapeType) {

        if (shapeType.equalsIgnoreCase("CIRCLE")) {
            return new Circle();
        } else if (shapeType.equalsIgnoreCase("RECTANGLE")) {
            return new Rectangle();
        } else if (shapeType.equalsIgnoreCase("SQUARE")) {
            return new Square();
        }
        return null;
    }
}
```
