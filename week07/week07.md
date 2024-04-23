# Week 07

## Dynamic Modelliing

UML supports interaction diagrams that can be used to show the dynamic behavior of software (i.e. how claases behave and interact, how dependencies manifest themselves)

Example of interaction diagrams:

- Sequence Diagrams
- Communication Diagrams
- Activity Diagram
- State Diagram

## Sequence Diagrams

### Object, Class

Objects are represented by boxes.

The label of the boxdescribes the object and / or class name in the following format:

> objectName : ClassName

### Lifeline, Activation Bar

A lifeline represents the object for the duration of its lifetime.

An activation bar is a thick bar overlay the lifeline of an object that indicates that the object is active involved in the system in that point of execution.

![lifeline and activation bar](/assets/uml_sequence_lifeline_activation_bar.png)

### Message

A message represents communication between objects in a system.

![message](/assets/uml_sequence_msg.png)

The client object (left) calls *aMethod* in the supplier object (right).

Parameter names are optional, but parameter and return types are required.

Objects can call messages on themselves, which is known as a reflexive message, and is depicted as follows:

![ref_message](/assets/uml_sequence_msg_ref.png)

### Creating Objects

We represent creation of a new object as follows:

![create](/assets/uml_sequence_create.png)

We can use either specify the method or use the `<<create>>` tag.

### Deleting objects and Termination of Lifelines

The end (termination) of an object's lifeline is marked with the `X` symbol.

We represent deletion of an object as follows:

![delete](/assets/uml_sequence_delete.png)

### Fragments

Fragments are used to group a collection of messages that represent a specific purpose.

![fragment](/assets/uml_sequence_fragment.png)

Types of fragments include:

- optional execution
- conditional execution
- iteration

Fragments can be nested inside one another, but it will make the diagram difficultto interpret.

#### Optional Execution

the `opt` / `optional` fragment indicates a part of the diagram that will be executed only if the supplied condition is True.

The condition is stated in a guard on the left side in square brackets.

![optional fragment](/assets/uml_sequence_frag_opt.png)

#### Conditional Execution

the `alt` / `alternative` fragment is similar to the optional fragment but with two or more alternatives instead of one.

The alternatives are seperated by a  horizontal dashed line.

![alternative fragment](/assets/uml_sequence_frag_alt.png)

#### Iteration

the `loop` fragment is used for parts of a system that runs in a loop

![loop fragment](/assets/uml_sequence_frag_loop.png)
