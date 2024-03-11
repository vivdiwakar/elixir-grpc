# Elixir meets gRPC

## How to get an Elixir client talking to a gRPC service

### Why use [gRPC](https://grpc.io) in the first place?

As the *RPC* in the name suggests, applications can interact with state on remote services/nodes via method invocations on these nodes - providing the building blocks for distributed and loosely-coupled applications and platforms.

The services, methods, argument and return types, and other parameters are precisely defined upfront, and the server then implements these methods as an *interface* and provides a service for clients to connect to; on the client side, the same definitions are used to create *stubs*, which provide the same methods as the server that can be invoked.

gRPC is language agnostic, meaning interfaces and stubs can be generated for any language that has a protobuf compiler and imported as libraries into the server and client implementations respectively.

Data between clients and servers is serialized using [Protocol Buffers](https://protobuf.dev/overview). Data structures are defined in plain-text *proto* files with a `.proto` extension, and these data structures can then be used in service and method definitions - also in proto files.

### When to use gRPC

gRPC is best suited for inter-component communication for a service backend, where the following are needed:

- Support for both synchronous and asynchronous calls including bidirectional streams
- Timeouts and back-pressure handling
- Low-latency, scalability and feature extendability
- Very good size reduction of serialized payloads over the wire
- Great for asynchronously offloading administrative elements of service meshes, like monitoring, logging, etc.

gRPC can be used for web/app communications to the server, though this requires additional plumbing and infrstructure like proxies and forwarders and browsers cannot at present easily talk to gRPC services over HTTP/2 natively.
