1. Explain the catchAsync wrapper pattern:

How does it simplify error handling in async route handlers?

In Express, errors thrown in async functions are not automatically caught and passed to error-handling middleware. The catchAsync pattern wraps async route handlers and automatically forwards any errors to Express’s error handler, so you don’t need to write repetitive try/catch blocks in every route.

2. What happens if an error is thrown inside a catchAsync wrapped function?

The error is caught and passed to the next middleware (usually the error handler) using next(error). This ensures consistent error handling throughout your app.

3. Why is this pattern important for production applications?

It prevents unhandled promise rejections, reduces boilerplate, and ensures all errors are handled in a centralized way, improving reliability and maintainability.

````js
// catchAsync utility
const catchAsync = fn => (req, res, next) => {
  Promise.resolve(fn(req, res, next)).catch(next);
};

// Usage in a route
app.get('/books/:id', catchAsync(async (req, res) => {
  const book = await Book.findById(req.params.id);
  res.json(book);
}));

````

4. How do you handle different types of errors in a REST API?


HTTP status codes for different error scenarios:

400 Bad Request: Invalid input or missing parameters.
401 Unauthorized: Authentication required or failed.
403 Forbidden: Authenticated but not allowed.
404 Not Found: Resource does not exist.
409 Conflict: Duplicate resource or state conflict.
500 Internal Server Error: Unexpected server error.
Providing meaningful error messages:

Include a clear message describing the error.
Optionally include an error code or details for debugging.
Avoid exposing sensitive information in production.

````js
{
  "status": "error",
  "message": "Book not found",
  "code": 404
}
````