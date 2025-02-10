# Unhandled Async Errors in Express.js

This repository demonstrates a common error in Express.js applications: failing to handle asynchronous errors properly, resulting in silent failures on the client-side.

## The Problem

The `bug.js` file shows an Express.js server with an asynchronous operation (`doSomethingAsync`) within a request handler.  If `doSomethingAsync` throws an error, the error is logged to the console, but **no error response is sent to the client.**  This leads to a frustrating user experience where requests seemingly vanish without explanation.

## The Solution

The `bugSolution.js` file demonstrates the correct way to handle this.  It uses a `try...catch` block within the asynchronous operation or utilizes async/await and a `catch` block to catch potential errors.  A proper error response is sent back to the client with a descriptive error message and a relevant HTTP status code (e.g., 500 Internal Server Error).

## How to reproduce

1. Clone this repository.
2. Navigate to the repository's directory.
3. Run `npm install express` to install the necessary dependencies.
4. Run `node bug.js` to start the server with the bug.
5. Make requests to `http://localhost:3000`. Observe that errors are logged to the console, but the client receives no response.
6. Run `node bugSolution.js` to start the fixed server.
7. Make requests to `http://localhost:3000`. Observe that errors are now handled gracefully, and the client receives informative error responses.
