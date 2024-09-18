# HTTP Request Methods

In this chapter, we will discuss the various HTTP request methods used for interacting with web APIs.

![HTTP Methods](HTTP-Methods.webp)

Image source: Dall-E by OpenAI

- [HTTP Request Methods](#http-request-methods)
  - [GET](#get)
  - [POST](#post)
  - [PUT](#put)
  - [DELETE](#delete)
  - [PATCH](#patch)
  - [OPTIONS](#options)
    - [Sources](#sources)

HTTP request methods are used to indicate the desired action to be performed on a resource identified by the URI (Uniform Resource Identifier) in the HTTP request.

## GET

**GET**: The GET method is used to retrieve a resource from the server. It is a safe and idempotent method, meaning that multiple identical requests have the same effect as a single request. The response to a GET request typically includes the requested resource or its representation in the message body.

```mermaid
sequenceDiagram
  participant Client as Client (Browser)
  participant Server as Web Server

  Note over Client,Server: Client wants to retrieve a resource.

  Client->>Server: GET /resource
  Server->>Client: 200 OK (Resource)
```

In this example, the client sends an `HTTP GET` request to the server to retrieve a resource. The server responds with a status code of `200 OK` along with the requested resource.

## POST

**POST**: The POST method is used to send data to the server to create or update a resource. It is not idempotent, meaning that multiple identical requests may have different effects. The response to a POST request typically includes the representation of the created or updated resource in the message body.

```mermaid
sequenceDiagram
  participant Client as Client (Browser)
  participant Server as Web Server

  Note over Client,Server: Client wants to create a new resource.

  Client->>Server: POST /resource (Resource data)
  Server->>Client: 201 Created (Resource)
```

In this example, the client sends an `HTTP POST` request to the server to create a new resource, providing the necessary data in the request body. The server responds with a status code of `201 Created` along with the newly created resource.

## PUT

**PUT**: The PUT method is used to update an existing resource on the server. It is idempotent, meaning that multiple identical requests have the same effect as a single request. The response to a PUT request typically includes the representation of the updated resource in the message body.

```mermaid
sequenceDiagram
  participant Client as Client (Browser)
  participant Server as Web Server

  Note over Client,Server: Client wants to update an existing resource.

  Client->>Server: PUT /resource/:id (Resource data)
  Server->>Client: 200 OK (Resource)
```

In this example, the client sends an `HTTP PUT` request to the server to update an existing resource, providing the necessary data in the request body. The server responds with a status code of `200 OK` along with the updated resource.

## DELETE

**DELETE**: The DELETE method is used to remove a resource from the server. It is idempotent, meaning that multiple identical requests have the same effect as a single request. The response to a DELETE request typically includes a confirmation message in the message body.

```mermaid
sequenceDiagram
  participant Client as Client (Browser)
  participant Server as Web Server

  Note over Client,Server: Client wants to delete an existing resource.

  Client->>Server: DELETE /resource/:id
  Server->>Client: 204 No Content
```

In this example, the client sends an `HTTP DELETE` request to the server to delete an existing resource. The server processes the request, deletes the resource, and responds with a status code of `204 No Content`.

## PATCH

**PATCH**: The PATCH method is used to partially update an existing resource on the server. It is not idempotent, meaning that multiple identical requests may have different effects. The response to a PATCH request typically includes the representation of the updated resource in the message body.

```mermaid
sequenceDiagram
  participant Client as Client (Browser)
  participant Server as Web Server

  Note over Client,Server: Client wants to partially update an existing resource.

  Client->>Server: PATCH /resource/:id (Partial resource data)
  Server->>Client: 200 OK (Resource)
```

In this example, the client sends an `HTTP PATCH` request to the server to partially update an existing resource, providing only the necessary data to be modified in the request body. The server processes the request, partially updates the resource, and responds with a status code of `200 OK` along with the updated resource.

## OPTIONS

The OPTIONS method is used to retrieve the available options for a resource. It is a safe and idempotent method, meaning that multiple identical requests have the same effect as a single request. The response to an OPTIONS request typically includes information about the supported methods, headers, and other options for the resource.

These HTTP request methods enable clients to interact with server resources in a standard and consistent manner, regardless of the specific implementation details of the server.

### Sources

- [HTTP Methods - MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
