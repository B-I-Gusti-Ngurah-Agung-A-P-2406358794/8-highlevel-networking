# Reflection

## 1. What are the key differences between unary, server streaming, and bidirectional streaming RPC?

Unary RPC means the client sends one request and the server returns one response. In this tutorial, PaymentService uses unary RPC because one payment request only needs one payment response.

Server streaming RPC means the client sends one request and the server can return multiple responses. In this tutorial, TransactionService uses server streaming because one transaction history request can return many transaction records.

Bidirectional streaming RPC means both client and server can send multiple messages continuously. In this tutorial, ChatService uses bidirectional streaming because the client can keep sending chat messages and the server can keep replying.

## 2. What are the potential security considerations when using gRPC in Rust?

Some important security considerations are authentication, authorization, and encryption. Authentication is needed to verify the user. Authorization is needed to make sure each user can only access allowed services or data. Encryption using TLS is also important so that data sent between client and server cannot be easily read by attackers.

## 3. What are the challenges of handling bidirectional streaming in Rust gRPC?

The main challenge is managing continuous communication between client and server. The program must handle multiple incoming and outgoing messages, closed connections, stream errors, and slow clients. Because it is asynchronous, the code also needs careful handling of tasks and channels.

## 4. What are the advantages and disadvantages of ReceiverStream?

ReceiverStream makes it easier to convert a Tokio channel receiver into a stream that can be returned by tonic. This is useful for server streaming and bidirectional streaming. However, developers still need to manage channel capacity, error handling, and task lifecycle carefully.

## 5. What improvements can be made to the code structure?

The code can be improved by separating each service into its own file or module, such as payment_service.rs, transaction_service.rs, and chat_service.rs. This would make the project easier to read, test, and maintain.

## 6. What additional logic could be added to PaymentService?

PaymentService could be improved by adding validation, database storage, authentication, transaction status, error handling, and integration with real payment providers.

## 7. How does gRPC help distributed systems?

gRPC helps distributed systems by providing a clear service contract using Protocol Buffers. It also supports efficient communication through HTTP/2 and is suitable for microservices that need fast and structured communication.

## 8. What is the difference between HTTP/2 used by gRPC and HTTP/1.1 used by many REST APIs?

HTTP/2 supports multiplexing, streaming, and header compression, which can improve performance. HTTP/1.1 is simpler and commonly used in REST APIs, but it is less efficient for continuous or high-performance communication.

## 9. What is the difference between REST request-response and gRPC bidirectional streaming?

REST usually follows a request-response pattern, where the client sends one request and receives one response. gRPC bidirectional streaming allows both client and server to send messages continuously in one connection, which is better for real-time features like chat.

## 10. What is the advantage of Protobuf compared to JSON?

Protobuf is schema-based, smaller, and more efficient for communication. JSON is easier for humans to read and more flexible, but it is usually larger and less strict than Protobuf.