# Week 12

## Technical Debt

> You have a piece of functionality that you need to add to your system. You see two ways to do it, one is quick to do but is messy - you are sure that it will make further changes harder in the future.  
> The other results in a cleaner design, but will take longer to put in place.  
> -Martin Fowler

Tehnical debt is time saved by making bad design decision in order to get a product / features out faster.

However, this will result in lower extensibility and maintainability in the future.

Technical debt can be "repaid" by refactoring code to become a better design.

![technical_debt](/assets/technical_debt.png)

### Mitigating Technical Debt

![technical_debt_situations](/assets/technical_debt_situations.png)

The above image shows that technical debt is okay when we are prudent about it, no matter if it was a deliberate or inadvertent decision.

## Design Process

Designing a software is sometimes seen as a creative act.

There are many approaches to software design, such as:

- brainstorming / model storming
- top down programming
- bottom up programming
- scenario based design
- CRC cards

### Brainstorming / Model Storming

A general approach to solving problems, requiring creativity in groups.

Model Storming is brainstorming but specific for software.

### Top Down Design

Start with high level problem, dividing it into sub-problems.

Design sub-problems and combine them.

However, may lead to repetition.

Pros:

- Starts with the needs of the organisation
- Provides a big picture to the customer and designer

Cons:

- Time consuming

### Bottom Up Design

Start with a small problem and design a solution for it.

Repeat multiple times and put them together.

Pros:

- Quick
- Leverages previous experience

Cons:

- Might miss some requirements
- Higher chance of failure

### Scenario Based Design

Have some scenarios that the software being designed needs to support. (e.g. storyboard, use case, activity diagram)

Work through the scenarios and design accordingly, modifying as needed to support each scenario effectively.

### CRC Cards

Uses **Class-Responsibility-Collaboration** cards to specify what a class does and how it does it with the help of outside factors (other classes).

Start with one or two obvious cards, and then work out the following classes / responsibilities from there onward based on made up scenarios.

![crc](/assets/crc.png)

Pros:

- help with encapsulation
- encourages small objects with clear responsibilities

Cons:

- Does not gurantee good design
- Not a good way to communicate design to outsiders (e.g. clients)
