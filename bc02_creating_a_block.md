### Challenge 2: Implementing a Basic Block Structure

This challenge is the second in a series that aims to guide you through the building blocks of a blockchain.

In a blockchain, each record is encapsulated within a "block." A block consists of a data section, the hash of the block, and the hash of the preceding block in the blockchain. This forms a linked list of blocks, commonly referred to as a blockchain. One crucial element in each block is its "hash," which you learned about in Challenge 1. The hash ensures that the block's content remains unaltered and verifies the sequence of blocks in the chain.

By participating in this challenge, you'll learn how to construct a basic block and how to utilize cryptographic hashing to secure its contents. The focus here is to grasp the fundamental structure of a block and understand its role within a blockchain.

#### Objective
Create a `Block` class that represents a basic building block of a blockchain. The aim is to understand how blocks store data and how they are linked together using hashes.

#### Requirements
- Node.js installed
- Basic knowledge of JavaScript classes
- Understanding of hashing (from Challenge 1)

#### Instructions
If you've completed Challenge 1, you already have a Node.js project set up with Jest for testing. If not, you can follow the same steps to set up your environment.

1. Create a new JavaScript file named `block.js`. 
2. Implement a `Block` class that should have the following properties:
    - `index`: The position of the block within the chain.
    - `timestamp`: A timestamp for when the block was created.
    - `data`: The data stored within the block.
    - `previousHash`: The hash of the previous block in the chain.
    - `hash`: The hash of the current block (this will be computed).
3. Include a method to calculate the hash of the block based on its properties. You'll use the `crypto-js` library for hashing.
4. Implement Jest tests to confirm that the `Block` class is functioning as expected. These tests should cover block creation, hashing, and any other functionality you deem necessary.

#### Deliverables
- A JavaScript file (`block.js`) containing a `Block` class with properties and methods relevant to a blockchain block.
- A Jest test file (`block.test.js`) to validate the functionality and integrity of your `Block` class.

#### Jest Tests Suggestions
1. Test whether the `Block` class can successfully instantiate a new block with given properties.
2. Verify that altering the `data` or `previousHash` of a block results in a change of its own hash.
3. Confirm that the hash generated for each block is unique unless the same input and previous hash are provided.
4. Check if the `Block` class correctly calculates the hash based on its properties.

By the end of this challenge, you should be well-versed in what a blockchain block is and how it works at a fundamental level. You'll also have a good grasp of how hashing ensures the block's integrity. This will prepare you for the next challenges, where you'll assemble these blocks into a working blockchain.
