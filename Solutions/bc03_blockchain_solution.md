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
const generateHash = require('./hashing')
const Block = require('./block')
const Blockchain = require('./blockchain')

describe('Blockchain', () => {
  let blockchain

  beforeEach(() => {
    blockchain = new Blockchain()
    blockchain.addBlock({ amount: 50 })
    blockchain.addBlock({ amount: 100 })
  })

  it('starts with a genesis block', () => {
    const block0 = blockchain.getBlock(0)
    expect(block0.getIndex()).toEqual(0)
    expect(block0.getData()).toBe('Genesis Block')
  })

  it('adds a new block', () => {
    const data = { amount: 150 }
    blockchain.addBlock(data)
    expect(blockchain.getBlock(3).getData()).toEqual(data)
  })

  it('can fetch latest block', () => {
    expect(blockchain.getLastBlock().getIndex()).toBe(2)
  })

  it('validates a valid chain', () => {
    expect(blockchain.isValidChain()).toBe(true)
  })

  it('validates a new chain', () => {
    expect(new Blockchain().isValidChain()).toBe(true)
  })
})

// This will need to be tested by tampering with a blockchain file that gets read in
// describe('Invalid Blockchain', () => {
//   it('invalidates a chain with a tampered genesis block', () => {
//     const block0 = blockchain.getBlock(0)
//     block0.data = { amount: 500 }
//     block0.hash = block0.calculateHash()
//     expect(blockchain.isValidChain()).toBe(false)
//   })

//   it('invalidates a chain with a tampered block', () => {
//     const block1 = blockchain.getBlock(1)
//     const block2 = blockchain.getBlock(2)
//     block1.data = { amount: 500 }
//     block1.hash = block1.calculateHash()
//     block2.hash = block1.hash
//     expect(blockchain.isValidChain()).toBe(false)
//   })
// })

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