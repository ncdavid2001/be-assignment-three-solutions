**1. What is the MVC (Model-View-Controller) pattern and how does it help organize code?**

The MVC pattern is a software architectural pattern that separates an application into three main components: Model, View, and Controller. This separation helps organize code by dividing responsibilities, making the application easier to develop, maintain, and scale. In Node.js APIs (without a UI), "View" is often omitted or replaced by API responses, but the separation between Model, Controller, and Service remains valuable.

**2. Explain the responsibilities of each component in the MVC pattern:**

Controller: Handles incoming HTTP requests, processes input, calls the appropriate service methods, and sends responses back to the client. It acts as the bridge between the client and the business logic.
Service: Contains the business logic of the application. It performs operations such as data validation, calculations, and orchestrates interactions between models and other services.
Schema/Model: Defines the data structure and rules for the application's data. It represents resources (like "Book" or "Todo") and handles data storage, retrieval, and validation.
Example:

````javascript
// Controller (books.controller.js)
exports.getBooks = (req, res) => {
  const books = bookService.getAllBooks();
  res.json(books);
};

// Service (books.service.js)
exports.getAllBooks = () => {
  return Book.findAll();
};

// Model (book.schema.js)
class Book {
  static findAll() {
    // logic to read books from storage
  }
}

````

**3. How does separating concerns in MVC make code more maintainable and testabl**

Maintainability: Each component has a single responsibility, so changes in one area (like data structure) don't affect others (like request handling).
Testability: You can test each layer independently. For example, you can test business logic in services without involving HTTP requests, and test controllers with mocked services.
Scalability: The clear separation allows teams to work on different parts of the application simultaneously and makes it easier to add new features or swap out implementations (e.g., changing the database layer).