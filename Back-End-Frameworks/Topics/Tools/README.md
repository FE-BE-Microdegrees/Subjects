# API Testing Tools

In this chapter, we will explore various tools that assist in creating and testing APIs.

![API tools](API-tools.webp)

Image source: Dall-E by OpenAI

- [API Testing Tools](#api-testing-tools)
  - [Learning Outcomes](#learning-outcomes)
  - [Postman](#postman)
  - [Thunder Client](#thunder-client)
  - [Command-Line Tool `curl`](#command-line-tool-curl)
  - [Docker Desktop](#docker-desktop)
  - [SQLTools VS Code Extension](#sqltools-vs-code-extension)

## Learning Outcomes

By the end of this chapter, you will be able to:

- Describe various tools that aid in the creation and testing of APIs.

Since web APIs typically support various request methods (`GET`, `POST`, `PUT`, `DELETE`, etc.), simply using a web browser to send requests to the API is no longer sufficient. Instead, dedicated tools are needed.

## Postman

Postman is an application specifically designed for API testing. With Postman, you can send different requests, view responses, save requests and responses, create various environments (e.g., development, testing, production), and more. You can also write tests in Postman to check that API responses are in the expected format.

Postman is available for download here: [Postman Downloads](https://www.postman.com/downloads/)

There is also a Postman extension available for VS Code, which can be found in the VS Code extensions marketplace.

## Thunder Client

Thunder Client is a free extension for the VS Code code editor that also allows for API testing.

You can download Thunder Client from the VS Code extensions marketplace.

## Command-Line Tool `curl`

`cURL` (Command-line URL) is a free and open-source software project that provides a command-line tool and library (libcurl) for transferring data using various protocols. `cURL` supports many internet protocols, including HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, LDAP, LDAPS, SMTP, POP3, IMAP, RTSP, and many others.

With `cURL`, you can effectively send various requests to an API and view responses.

For example, sending a `GET` request:

```bash
curl http://localhost:3000/
```

Or sending a `POST` request:

```bash
curl -X POST -H "Content-Type: application/json" -d '{"username":"xyz","password":"xyz"}' http://localhost:3000/login
```

## Docker Desktop

`Docker Desktop` is an application that allows developers to build, test, and share applications in containers. Containers are lightweight, isolated, and reusable virtual environments that provide developers the ability to develop and run applications anywhere Docker is available.

## SQLTools VS Code Extension

`SQLTools` is a popular Visual Studio Code (VS Code) extension that offers a powerful and user-friendly SQL database management tool directly within the VS Code environment. It allows developers to write and execute SQL queries, manage databases, and view data results without leaving VS Code. `SQLTools` supports several database management systems, including MySQL, PostgreSQL, SQLite, and many others.
