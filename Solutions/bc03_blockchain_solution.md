### Challenge 3 Solution
#### Step 1: Setup
Make sure you have completed the previous challenges, as you'll be building upon them. If you haven't, follow the setup instructions in the previous solutions to initialize a new Node.js project and set up Jest for testing.

#### Step 2: Create the Blockchain Class

Create a new file named `blockchain.js`. Import the `Block` class from your `block.js` file. Initialize your `Blockchain` class with a genesis block and add methods to add blocks and validate the chain.

Here's a basic skeleton:

```javascript
const Block = require('./block');

class Blockchain {
  constructor() {
    this.chain = [this.createGenesisBlock()];
  }

  createGenesisBlock() {
    return new Block(0, Date.now(), "Genesis block", "0");
  }

  addBlock(data) {
    // add date and new block # here
    // call block here
    newBlock.previousHash = this.chain[this.chain.length - 1].hash;
    newBlock.hash = newBlock.calculateHash();
    this.chain.push(newBlock);
  }

  validateChain() {
    for (let i = 1; i < this.chain.length; i++) {
      const currentBlock = this.chain[i];
      const previousBlock = this.chain[i - 1];

      if (currentBlock.hash !== currentBlock.calculateHash()) {
        return false;
      }

      if (currentBlock.previousHash !== previousBlock.hash) {
        return false;
      }
    }

    return true;
  }
}

module.exports = Blockchain;
```

#### Step 3: Writing Jest Tests

Create another file named `blockchain.test.js`. Here, write some Jest tests to validate the `Blockchain` class methods.

```javascript
const { Block, Blockchain } = require('./blockchain'); // Assume both classes are exported from blockchain.js

describe('Blockchain', () => {
  let blockchain;

  beforeEach(() => {
    blockchain = new Blockchain();
    blockchain.addBlock(new Block(1, '02/01/2023', { amount: 50 }));
    blockchain.addBlock(new Block(2, '03/01/2023', { amount: 100 }));
  });

  it('starts with a genesis block', () => {
    expect(blockchain.chain[0]).toEqual(blockchain.createGenesisBlock());
  });

  it('adds a new block', () => {
    const data = 'some data';
    blockchain.addBlock(new Block(1, '01/02/2021', data, ''));
    expect(blockchain.chain[1].data).toEqual(data);
  });

  it('validates a valid chain', () => {
    blockchain.addBlock(new Block(1, '01/02/2021', 'some data', ''));
    expect(blockchain.validateChain()).toBe(true);
  });
  
  it('validates a valid chain', () => {
    expect(blockchain.isValidChain()).toBe(true);
  });

  it('invalidates a chain with a tampered genesis block', () => {
    blockchain.chain[0].data = { amount: 500 };
    blockchain.chain[0].hash = blockchain.chain[0].calculateHash();
    expect(blockchain.isValidChain()).toBe(false);
  });

  it('invalidates a chain with a tampered block', () => {
    blockchain.chain[1].data = { amount: 500 };
    blockchain.chain[1].hash = blockchain.chain[1].calculateHash();
    expect(blockchain.isValidChain()).toBe(false);
  });

  it('invalidates a corrupt chain', () => {
    blockchain.addBlock(new Block(1, '01/02/2021', 'some data', ''));
    blockchain.chain[1].data = 'tampered data';
    expect(blockchain.validateChain()).toBe(false);
  });
});
```

Run your tests by executing:

```bash
npm test
```

You should see Jest output indicating whether your tests have passed or failed.

These tests cover:

- Checking that the blockchain initializes with a genesis block.
- Adding a new block.
- Validating the blockchain when it is valid.
- Invalidating the blockchain if the genesis block or another block has been tampered with.

Congratulations, you've successfully created a basic blockchain in JavaScript!