**1. What are the core principles of REST architecture and how do they apply to API design?**


REST (Representational State Transfer) is an architectural style for designing networked applications. Its core principles are:

Statelessness: Each request from a client contains all the information needed to process it. The server does not store client context between requests.
Client-Server Separation: The client and server are independent; the client handles the UI, and the server manages data and logic.
Uniform Interface: Resources are accessed and manipulated using a consistent set of URLs and HTTP methods.
Resource-Based: Everything is treated as a resource, identified by a URL (e.g., /books/1).
Representation: Resources can have different representations (JSON, XML, etc.), and clients interact with these representations.
Cacheability: Responses must define themselves as cacheable or not to improve performance.

**2. Explain the difference between GET, POST, PUT, and DELETE HTTP methods. When would you use each?**


GET: Retrieves data from the server. Used for reading resources (e.g., GET /books to list all books).
POST: Creates a new resource on the server. Used when submitting data (e.g., POST /books to add a new book).
PUT: Updates an existing resource or creates it if it does not exist. Used for full updates (e.g., PUT /books/1 to replace book 1).
DELETE: Removes a resource from the server (e.g., DELETE /books/1 to delete book 1).


**3. How do you structure RESTful endpoints for a resource like "books" or "todos"?**

RESTful endpoints use nouns (not verbs) and represent resources and their collections. Example structure for "books"

GET    /books        // List all books
POST   /books        // Create a new book
GET    /books/:id    // Get a specific book by ID
PUT    /books/:id    // Update a specific book by ID
DELETE /books/:id    // Delete a specific book by ID

How do you structure RESTful endpoints for a resource like "books" or "todos"?