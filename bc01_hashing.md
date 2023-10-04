### Challenge 1: Introduction to Hashing with `crypto-js`

This challenge is the first in a series that will show you how blockchains are constructed. 

This first challenge is about hashing. A hash is the output of a hash function, which is a mathematical algorithm that takes an input (or "message") and returns a fixed-size string of characters, which appear random. The output, or hash value, should be the same length regardless of the length of the input. Hash functions are commonly used in many applications, including data verification, password storage, and cryptography.

In blockchains, cryptographic hashing plays a pivotal role in ensuring data integrity and security. Each block in a blockchain contains a cryptographic hash of the previous block, creating an interlinked chain. This hash function takes an input (or 'message') and returns a fixed-size string of characters, which is typically a 'digest' that represents the input data. Hashing is a one-way function, making it computationally infeasible to regenerate the original input value given the hash output. This makes blockchains resistant to modification, as altering any single block would require recalculating the hash for all subsequent blocks. 

This first challenge will familiarize you with what a hash algorithm is, and how to apply it to some data. 

#### Objective
Learn how to use the `crypto-js` library to generate SHA-256 hashes. The primary goal is to understand how different inputs produce unique hash outputs.

#### Requirements
- Node.js installed

#### Instructions
1. Initiate a new JavaScript project named `blockchain` using `npm init`. Then, install `crypto-js` via npm, and configure the project for Jest.js testing.
2. Create a new file, `hashing.js`. Import the `SHA256` function from `crypto-js` and write a function named `generateHash`. This function should accept any input, convert it to a string, and return its SHA-256 hash.
3. Implement and run Jest tests based on the suggestions below to validate your `generateHash` function.

#### Deliverables
- A JavaScript file (`hashing.js`) that houses the function for generating SHA-256 hashes.
- A Jest test file (`hashing.test.js`) to confirm your hashing function's functionality.

#### Jest Test Suggestions
1. Test if the `generateHash` function yields a consistent hash for identical string inputs.
2. Verify that the `generateHash` function produces unique hashes for different strings.
3. Check that the `generateHash` function generates distinct hashes for similar values but of different types (e.g., '123' and 123).

This first challenge will ground you in the concept of hashing and its applications, setting the stage for the next challenge, where you'll learn about the basic structure of a blockchain block.