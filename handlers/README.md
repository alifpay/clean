4. Handlers any transport layer http web api, grpc, graphql and etc.

Handlers are responsible for receiving requests from clients and sending responses back to to clients. HTTP+JSON and gRPC are two kinds of transports, for example. By not allowing transport specific details to leak into the business logic, a service can plug in transports for any number of protocols and hand off processing to pure business logic that is not concerned with communicating with clients.

Messaging and streaming system, gRPC, graphQL, REST API, WEB API