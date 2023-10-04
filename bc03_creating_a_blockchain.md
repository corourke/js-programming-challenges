### Challenge 3: Creating and Validating a Simple Blockchain

In the previous challenges, you've learned about hashing and created a basic block structure. Now, let's put these blocks into a chain to form a basic blockchain. A blockchain is a continuous series of blocks (also known as a chain), which contain data and are linked and secured using cryptographic hashes.

#### Objective

Learn how to build a simple blockchain structure in JavaScript. Understand the importance of validating new blocks and maintaining the integrity of the entire chain.

#### Requirements

- Node.js installed
- Completion of the previous challenges (or at least have the basic `Block` class and hashing function ready)

#### Instructions
Make sure you have completed the previous challenges, as you'll be building upon them. If you haven't, follow the setup instructions in the previous solutions to initialize a new Node.js project and set up Jest for testing.

1. Create a new JavaScript file named `blockchain.js`.
2. Inside `blockchain.js`, import the `Block` class you created in Challenge 2.
3. Create a `Blockchain` class that initializes with a genesis block and adds it to a chain.
4. Implement methods to `addBlock` and `validateChain`.

#### Jest Test Suggestions:

1. Validate that the blockchain starts with a genesis block.
2. Check if `addBlock` actually adds a block to the chain.
3. Confirm that `validateChain` correctly identifies a valid chain.
4. Confirm that `validateChain` correctly identifies an invalid chain (e.g., by manually altering a previous block's data or hash and checking if the chain is still valid).

#### Deliverables

- A JavaScript file (`blockchain.js`) containing the `Blockchain` class, complete with methods to add blocks and validate the chain.
- A Jest test file (`blockchain.test.js`) confirming the functionality of your blockchain methods.

After you complete this challenge, you should have a basic, but functional, blockchain model.
