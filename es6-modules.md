1. Compare CommonJS (require/module.exports) vs ES6 modules (import/export):
Syntax differences
````js
// Export
module.exports = myFunction;
// or
exports.myFunc = myFunc;

// Import
const myFunction = require('./myModule');


// Export
export default myFunction;
export const myFunc = () => {};

// Import
import myFunction from './myModule.js';
import { myFunc } from './myModule.js';
````
Advantages of ES6 modules:

Static analysis (enables tree-shaking and better tooling)
Cleaner, more standardized syntax (used in browsers and modern JS)
Supports both named and default exports
Encourages modular, maintainable code
How to configure Node.js to use ES6 modules:

Set "type": "module" in your package.json
Use .js file extensions for imports (e.g., import x from './file.js')
Alternatively, use .mjs file extensions
Explain the different types of exports:
Named exports: Export multiple values by name.

Usage: When you want to export several functions, constants, or classes from a module.
Example:

````js
// Export
export const foo = () => {};
export const bar = 42;

// Import
import { foo, bar } from './myModule.js';
````

Default export: Export a single value as the default export.

Usage: When your module has one main thing to export (e.g., a class or function).
Example:

````js
// Export
export default function main() {}

// Import
import main from './myModule.js';

````

When to use each:

Use default export for the primary value of a module.
Use named exports for utility modules or when exporting multiple values.
How to import:

Default export: import myValue from './module.js'
Named export: import { myValue } from './module.js'
Both: import myValue, { anotherValue } from './module.js'
