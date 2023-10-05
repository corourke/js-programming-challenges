### Challenge 1 Solution
#### Step 1: Setup
Initialize a new Node.js project and install the `crypto-js` package:

```bash
mkdir blockchain-js
cd blockchain-js
npm init -y
npm install crypto-js
```

To add Jest for testing, run:

```bash
npm install --save-dev jest
```

Then modify your `package.json` to include a test script:

```json
"scripts": {
  "test": "jest"
}
```

#### Step 2: Create a Hashing Function

Create a new file named `hashing.js`. Import the `SHA256` function from `crypto-js` and create a function `generateHash` that takes any kind of input, converts it to a string, and returns its SHA-256 hash.

`hashing.js`
```javascript
const SHA256 = require('crypto-js/sha256')

function generateHash(input) {
  const data = typeof input == 'string' ? input : JSON.stringify(input)
  return SHA256(data).toString()
}

module.exports = generateHash
```

#### Step 3: Writing Jest Tests

Create another file named `hashing.test.js`. Here, we'll write some Jest tests to validate the `generateHash` function.

`hashing.test.js`
```javascript
const generateHash = require('./hashing')

describe('Hashing Function', () => {
  it('generates a consistent hash from the same string', () => {
    const hash1 = generateHash('Hello World')
    const hash2 = generateHash('Hello World')
    expect(hash1).toEqual(hash2)
  })

  it('generates a unique hash for different strings', () => {
    const hash1 = generateHash('Hello World')
    const hash2 = generateHash('Hello World!')
    expect(hash1).not.toEqual(hash2)
  })

  it('should stringfy non-strings', () => {
    const hash1 = generateHash('123')
    const hash2 = generateHash(123)
    expect(hash1).toEqual(hash2)
  })

  it('generates a consistent hash for javascript object vs. stringified object', () => {
    const obj1 = [
      { id: 0, type: 'send', addr: 'e322' },
      { id: 1, type: 'recv', addr: '88f2' },
    ]
    const hash1 = generateHash(obj1)
    const hash2 = generateHash(JSON.stringify(obj1))
    expect(hash1).toEqual(hash2)
  })
})
```

These tests cover the following:
- Consistency: The same input should always produce the same hash.
- Uniqueness: Different inputs should produce different hashes.
- Type Sensitivity: Non-string types should be converted (like '123' and 123) and produce same hashes.

Run your tests by executing:

```bash
npm test
```

You should see Jest output indicating whether your tests have passed or failed.