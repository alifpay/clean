Clean Architecture in Go. Develop clean Go code that is easier to read, maintain, and test.

![Clean Architecture on Golang](/imgs/codestr.jpg)


1. Dependency injection (DI) is coding in such a way that those resources (that is, functions or structs) that we depend on are abstractions. Because these dependencies are abstract, changes to them do not necessitate changes to our code. The fancy word for this is decoupling. DI is a tool — a handy tool, but no magic bullet. It's a tool that can make code easier to understand, test, extend, and reuse — a tool that can also help reduce the likelihood of circular dependency issues that commonly plague new Go developers.

(https://en.wikipedia.org/wiki/Dependency_injection) 
Dependency injection is a technique whereby one object supplies the dependencies of another object. A "dependency" is an object that can be used, for example as a service. Instead of a client specifying which service it will use, something tells the client what service to use. The "injection" refers to the passing of a dependency (a service) into the object (a client) that would use it. The service is made part of the client's state. Passing the service to the client, rather than allowing a client to build or find the service, is the fundamental requirement of the pattern. 

The intent behind dependency injection is to achieve Separation of Concerns of construction and use of objects. This can increase readability and code reuse.

Dependency injection is one form of the broader technique of inversion of control. A client who wants to call some services should not have to know how to construct those services. Instead, the client delegates the responsibility of providing its services to external code (the injector). The client is not allowed to call the injector code;[2] it is the injector that constructs the services. The injector then injects (passes) the services into the client which might already exist or may also be constructed by the injector. The client then uses the services. This means the client does not need to know about the injector, how to construct the services, or even which actual services it is using. The client only needs to know about the intrinsic interfaces of the services because these define how the client may use the services. This separates the responsibility of "use" from the responsibility of "construction". 

2. Business layer in controller

Business logic or domain logic is that part of the program which encodes the real-world business rules that determine how data can be created, stored, and changed. It prescribes how business objects interact with one another, and enforces the routes and the methods by which business objects are accessed and updated.

3. Storage (Database and caches)  
Storage is responsible for database related job such as querying, inserting/storing or deleting. No business logic is implemented here.
Repositories abstract data storage behind a common interface, allowing services to persist data to and retrieve data from any number or type of storage backends.

4. Handler any transport layer http web api, grpc, graphql and etc.

Handler is responsible for receiving requests from clients and sending responses back to clients. HTTP+JSON and gRPC are two kinds of transports, for example. By not allowing transport specific details to leak into the business logic, a service can plug in transports for any number of protocols and hand off processing to pure business logic that is not concerned with communicating with clients.

5. Gateway is external services

Gateway provides a standard mechanism for communicating with external services (e.g., payment, email).

Purpose:

   Consistent Code Structure, easy to understand, navigate and reason about, easy to change, loosely-coupled. Easy test. As simple as possible, but not simpler. Design reflects exactly how the software works, structure reflects the design exactly.

