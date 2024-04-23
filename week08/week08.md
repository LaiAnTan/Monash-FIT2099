# Week 08

## Design by Contract, DbC

The Design by Contract is an approach for designing software. It views software design as **a set of communicating components whose interaction is based on the defined specification of mutual obligations**.

### Central Idea

The central idea of DbC is based on how software systems collaborate with each other on the basis of mutual obligation and benefits.

The metaphor comes from a business standpoint, where a **"client"** and a **"supplier"** agree on a **"contract"**.

### Client, Supplier

In DbC, a supplier provides services to a client.

The client-supplier relationship is shown as an association or dependency in a UML Class diagram.

### Contract

The contract is defined by the designer of the supplier class.

It is communicated to the user of the supplier class via:

- documentation and comments
- executable statements

The contract should cover:

- what the client needs to provide to the class (preconditions)
- what the supplier will gurantee to be true if the class is used correctly (postconditions)

#### Preconditions and Postconditions

Preconditions are the conditions that the client must satisfy before the supplier's methods are used.

Postconditions are the services that the supplier gurantees to provide.
Postconditions describe things that are true after the supplier's methods are executed.

![example](/assets/dbc.png)

### Invariant

An invariant is something that is guranteed by the class to be true at all times.

The invariant must be true both before and after any supplier method is called.

### Breach of Contract

There are different ways that a contract can be breached.

a) Precondition violated -> client is at fault

- an exception should be thrown to the caller

b) Postcondition / Invariant violated -> supplier is at fault

- issue should be resolved in the called method

### Subcontracting

Subcontracting is when a client uses a service done by a subcontractor.

The client can use the subcontractor's serivce if and only if:

- the preconditions are the same or weaker than the original

- the postconditions are the same or stronger that the original

For example, consider the following code:

```java
// Define a Supplier
class Supplier {
    public void supply() {
        System.out.println("Supplying resources");
    }
}

// Define a Subcontractor
class Subcontractor extends Supplier {

    // additional postconditions
    @Override
    public void supply() {
        super()
        System.out.println("Subcontractor supplying additional resources");
    }
}

// Define a Concrete Client
class Client implements Client {
    public void requestResources(Supplier supplier) {
        supplier.supply();
    }
}

public class Main {
    public static void main(String[] args) {
        Client client = new Client();
        Supplier supplier = new Supplier();
        Subcontractor subcontractor = new Subcontractor();

        // Client using Supplier
        client.requestResources(supplier);

        // Client can use Subcontractor because it provides the same postconditions
        client.requestResources(subcontractor);
    }
}
```

In this case, the client class can use the subcontractor class as it provides more ponstconditions than the original supplier class.

## Fast Fail Principle

A good principle for engineering reliable software.

> If code detects an error, it must fail immediately.

## Command-Query-Seperation Principle

The Command-Query-Seperation Principle states that every method should either be a **command** or a **query**.

Commands (Mutator) - Change the state of a system but do not return a value.

Queries (Assesor) - Return a result and do not change the observable state of the system (are free of side effects).
