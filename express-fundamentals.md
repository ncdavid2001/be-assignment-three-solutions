1. What is Express.js and how does it simplify Node.js web application development?

Express.js is a minimal and flexible web application framework for Node.js. It provides a robust set of features for building web and API applications, such as routing, middleware support, and HTTP utility methods. Express simplifies Node.js development by abstracting away much of the low-level HTTP handling, allowing developers to write cleaner, more maintainable code with less boilerplate. For example, instead of manually parsing request data and handling routes, you can define routes and use middleware functions with simple, readable syntax.

2. Explain the difference between middleware and route handlers in Express.js.

Middleware are functions that have access to the request (req), response (res), and the next middleware in the stack (next). They can modify the request/response objects, end the request-response cycle, or pass control to the next function. Middleware is used for tasks like logging, authentication, parsing JSON, etc.
Route handlers are specific middleware functions that respond to HTTP requests for a particular route and method (e.g., GET /books). They typically send a response to the client and end the request-response cycle.

3. How does Express.js handle HTTP requests and responses differently from vanilla Node.js?

In vanilla Node.js, you must manually parse URLs, handle HTTP methods, and construct responses using the core http module. This often leads to repetitive and verbose code. Express.js wraps the Node.js HTTP objects and provides a higher-level API, making it easier to define routes, parse request bodies, set headers, and send responses. Express also manages the routing and middleware stack for you, so you can focus on application logic rather than low-level HTTP details.

````javascript
// Vanilla Node.js
const http = require('http');
http.createServer((req, res) => {
  if (req.url === '/books' && req.method === 'GET') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ books: [] }));
  }
}).listen(3000);

// Express.js
const express = require('express');
const app = express();
app.get('/books', (req, res) => {
  res.json({ books: [] });
});
app.listen(3000);

````