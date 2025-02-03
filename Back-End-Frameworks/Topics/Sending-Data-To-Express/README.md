# Sending Data to an Express Application

In this chapter, we will explore how to send data to an Express application.

![Sending Data to an Express Application](Sending-Data-To_express.webp)

Image source: Dall-E by OpenAI

- [Sending Data to an Express Application](#sending-data-to-an-express-application)
  - [Learning Outcomes](#learning-outcomes)
  - [Query Parameters (_req.query_)](#query-parameters-reqquery)
  - [Request Body (_req.body_)](#request-body-reqbody)
  - [URL Parameters (_req.params_)](#url-parameters-reqparams)
  - [Headers](#headers)
  - [Summary](#summary)

## Learning Outcomes

After completing this chapter, you will be able to:

- Describe different ways to send data to an Express application.
- Explain how to send query parameters, request bodies, URL parameters, and headers to an Express application.

When developing a dynamic website or API using the Express framework, it is essential to understand how to send data to the application.

There are multiple ways to send data to an Express application.

## Query Parameters (_req.query_)

Query parameters allow data to be sent via the URL. For example, to send a search query, you might use a URL like `/search?q=example`. In an Express application, you can access query parameters using the `req.query` object.

```javascript
...
app.get('/search', (req, res) => {
  const query = req.query.q;
  res.send(`Search query: ${query}`);
});
...
```

In this example, we configure an Express application that listens for GET requests on the `/search` route. When a request is made, we access the query parameter `q` using `req.query` and return it as the response.

## Request Body (_req.body_)

Data in the request body is usually sent using methods like POST, PUT, and DELETE. In Express, you can access the request body using middleware.

By default, the `req` object in Express does not have a `body` property, which typically contains the request body content. To enable this feature, middleware must be used. The following example demonstrates how to add middleware to parse incoming JSON and URL-encoded data:

```javascript
const express = require("express");
const app = express();

const port = 3000;

app.use(express.json());
app.use(express.urlencoded({ extended: true }));
```

These `app.use` statements register the middleware that adds the `body` property to the `req` object, allowing access to the request body.

In the following example, the client sends a `POST` request to the `/students/add` endpoint with the following JSON object:

```json
{
  "firstName": "Angus",
  "lastName": "Ingram",
  "curriculum": "RIF22"
}
```

The Express application handles the request as follows:

```javascript
...
app.post('/students/add', (req, res) => {
  const student = req.body;
  console.log(student);
});
...
```

Output:

```bash
{
  firstName: 'Angus',
  lastName: 'Ingram',
  curriculum: 'RIF22'
}
```

## URL Parameters (_req.params_)

Data can also be sent via URL parameters. For example, to send a product ID, you can use a URL like `/products/:id`. In an Express application, you can access URL parameters using the `req.params` object.

```javascript
...
app.get('/users/:id', (req, res) => {
  const userId = req.params.id;
  res.send(`User ID: ${userId}`);
});
...
```

In this example, we configure an Express application that listens for GET requests on the `/users/:id` route. When a request is made, we access the ID parameter using `req.params`. The response contains the user ID received in the request.

> Note that `:id` in the route represents a variable that becomes a property in the `req.params` object.

## Headers

Data can also be sent using request headers, for example, authentication tokens or metadata. In an Express application, headers can be accessed using `req.headers`.

Headers are commonly used in Express applications for authentication, security, content type specification, and more. In APIs, headers are often used to send a JWT token, allowing the API to identify the user and verify permissions.

```javascript
...
app.get('/headers', (req, res) => {
  const { headers } = req;
  res.send(headers);
});
...
```

In this example, we configure an Express application that listens for GET requests on the `/headers` route. When a request is made, we access all headers using `req.headers` and return them in the response.

For authentication and authorization, JWT tokens are typically sent in the `Authorization` header with the format `Bearer <token>`. Using Thunder Client, the request might look like this:

![Send JWT](image.png)

The response to this request might look like this:

```json
{
  "content-length": "57",
  "accept-encoding": "gzip, deflate, br",
  "accept": "*/*",
  "user-agent": "Thunder Client (https://www.thunderclient.com)",
  "authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwicm9sZSI6IkFkbWluIiwiaWF0IjoxNzA0Mjk2NjczLCJleHAiOjE3MDQzMDAyNzN9.fuJW0xbU-EtfpfuJatn2eqkCg7m1QKXth98eg7znJP4",
  "content-type": "application/json",
  "host": "localhost:3000",
  "connection": "close"
}
```

Now, the API can extract the token from the headers and use it for authentication.

## Summary

As we have seen, there are multiple ways to send data to an Express application. Each method has its use cases, and they can be combined to achieve the desired outcome. Understanding how to send data properly allows developers to build more efficient and functional APIs.
