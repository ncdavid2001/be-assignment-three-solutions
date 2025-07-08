1. Compare and contrast in-memory storage vs. file-based storage:


In-memory storage:

Advantages: Very fast read/write operations; simple to implement; ideal for temporary or test data.
Disadvantages: Data is lost when the application restarts or crashes; not suitable for persistent data; limited by available RAM.
When to use: For caching, testing, or applications where data persistence is not required.


File-based storage:

Advantages: Data persists across application restarts; easy to implement using JSON or text files; no external database required.
Disadvantages: Slower than in-memory; can have issues with concurrent access (race conditions); not scalable for large datasets.
When to use: For small projects, prototypes, or when you need simple persistence without a database.
Data persistence and application restart:

In-memory: All data is lost on restart.
File-based: Data is saved to disk and reloaded on restart, so it persists.

**2. Explain the file-based database implementation:
How does the readFromFileDb() function work?**

It reads data from a JSON file on disk (usually using fs.readFileSync or fs.promises.readFile), parses the JSON, and returns the data as a JavaScript object or array.

What happens when the JSON file doesn't exist?

The function should handle the error (e.g., ENOENT for "file not found") and return an empty array or object as the initial state, then create the file when data is first saved.


3. How do you handle concurrent access to the same file?

File-based storage is prone to race conditions if multiple operations happen at once. To handle this:
Use file locks or queues to serialize read/write operations.
Use atomic write techniques (write to a temp file, then rename).
For simple apps, use synchronous file operations to avoid overlap, but this can block the event loop and is not scalable.


````js
// Example readFromFileDb implementation
const fs = require('fs');
function readFromFileDb(filePath) {
  try {
    const data = fs.readFileSync(filePath, 'utf-8');
    return JSON.parse(data);
  } catch (err) {
    if (err.code === 'ENOENT') return []; // File doesn't exist
    throw err;
  }
  ````