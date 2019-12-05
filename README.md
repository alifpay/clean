Clean Architecture on Golang. Develop clean Go code that is easier to read, maintain, and test.

1. Dependency injection (DI) is coding in such a way that those resources (that is, functions or structs) that we depend on are abstractions. Because these dependencies are abstract, changes to them do not necessitate changes to our code. The fancy word for this is decoupling. DI is a tool — a handy tool, but no magic bullet. It's a tool that can make code easier to understand, test, extend, and reuse — a tool that can also help reduce the likelihood of circular dependency issues that commonly plague new Go developers.

2. Business layer in controllers

Business logic or domain logic is that part of the program which encodes the real-world business rules that determine how data can be created, stored, and changed. It prescribes how business objects interact with one another, and enforces the routes and the methods by which business objects are accessed and updated.

3. Storages (Database and caches)  
Storage is responsible for database related job such as querying, inserting/storing or deleting. No business logic is implemented here.
Repositories abstract data storage behind a common interface, allowing services to persist data to and retrieve data from any number or type of storage backends.

4. Handlers any transport layer http web api, grpc, graphql and etc.

Handlers are responsible for receiving requests from clients and sending responses back to to clients. HTTP+JSON and gRPC are two kinds of transports, for example. By not allowing transport specific details to leak into the business logic, a service can plug in transports for any number of protocols and hand off processing to pure business logic that is not concerned with communicating with clients.

5. Gateways are external services

Gateways provide a standard mechanism for communicating with external services (e.g., payment, email).

Purpose:

   Consistent Code Structure, easy to understand, navigate and reason about, easy to change, loosely-coupled. Easy test. As simple as possible, but not simpler. Design reflects exactly how the software works, structure reflects the design exactly.

