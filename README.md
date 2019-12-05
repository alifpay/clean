Clean Architecture on Golang. Develop clean Go code that is easier to read, maintain, and test.

1. Dependency injection (DI) is coding in such a way that those resources (that is, functions or structs) that we depend on are abstractions. Because these dependencies are abstract, changes to them do not necessitate changes to our code. The fancy word for this is decoupling. At the end of the day, DI is a tool — a handy tool, but no magic bullet. It's a tool that can make code easier to understand, test, extend, and reuse — a tool that can also help reduce the likelihood of circular dependency issues that commonly plague new Go developers.

2. Business layer in controllers

Let's start with some basic definitions, and then look at a couple of examples and see how those definitions map to the examples, and how they map to actual software.

Business logic or domain logic is that part of the program which encodes the real-world business rules that determine how data can be created, stored, and changed. It prescribes how business objects interact with one another, and enforces the routes and the methods by which business objects are accessed and updated.

Business Rules describe the operations, definitions and constraints that apply to an organization. The operations collectively form a process; every business uses these processes to form systems that get things done.

Now, let's work with some examples.
Transferring money from one checking account to another

First, what are the things that you need to know (input)?

    The identity of the person making the transfer
    The amount of money to be transferred
    The source checking account number
    The target checking account number

What are some of the "business rules" that must be applied?

    The person making the request must have the authority to do so.
    The transaction must be atomic.
    The transaction may have reporting requirements to the government, if it is over a certain amount

By "atomic," I mean that the transaction must completely succeed or it must completely fail. You can't have account transactions where money is taken out of one account without arriving in the other (money disappears), or money is deposited into an account, but not debited from another account (money magically appears from nowhere).
Ordering something from Amazon.

What do you need to know?

    The identity of the person ordering
    Shipping information
    Billing information
    Method of Payment
    Amount and quantity of each item to ship
    How to ship (overnight, slow boat or super saver)
    State Tax Rate

What happens after the order is placed?

    Items are pulled from stock
    On hand quantities are debited
    Items are packaged for shipment
    Out of stock items are backordered
    Items that drop below minimum quantities are ordered
    One shipment or two?

    An invoice/shipping list is printed, and placed with the order

3. Storages (Database and caches)  
Storage is responsible for database related job such as querying, inserting/storing or deleting. No business logic is implemented here.
Repositories abstract data storage behind a common interface, allowing services to persist data to and retrieve data from any number or type of storage backends.

4. Handlers any transport layer http web api, grpc, graphql and etc.

Handlers are responsible for receiving requests from clients and sending responses back to to clients. HTTP+JSON and gRPC are two kinds of transports, for example. By not allowing transport specific details to leak into the business logic, a service can plug in transports for any number of protocols and hand off processing to pure business logic that is not concerned with communicating with clients.

5. Gateways any services

Gateways provide a standard mechanism for communicating with external services (e.g., payment, email).

Purpose:
Consistent Code Structure
Easy to understand, navigate and reason about
Easy to change, loosely-coupled.
Easy test
As simple as possible, but not simpler
Design reflects exactly how the software works
Structure reflects the design exactly.

