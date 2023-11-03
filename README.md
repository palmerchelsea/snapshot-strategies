# Snapshot strategies

### Development

#### Install dependencies
```bash
yarn
```

#### Build package
```bash
yarn build
```

#### Test strategy 
*Note: If you're writing a new strategy, make sure to add it to strategies/index.ts before testing*
```bash
# Test default strategy (erc20-balance-of)
yarn test
# Test strategy with name
yarn test --strategy=erc20-received
yarn test --strategy=eth-balance
# Test with more addresses from addresses.json
yarn test --strategy=eth-balance --more=200
```

Checklist for adding a new strategy
Here is a simple checklist to consider when reviewing a PR for a new strategy:

Overview

- The strategy must be unique.
- If the strategy performs only a single call with an address as input, it's preferable to use the strategy "contract-call" instead of creating a new one.

Code

- There should be a maximum of 5 requests; a request can use "fetch," "subgraphRequest," or "multicall."
- The strategy should not send a request for each voter, as this doesn't scale.
- The strategy PR should not add any external dependencies to Snapshot.js.
- The score returned by the strategy should use the same casing for the address as the input or should return checksummed addresses.

Example

- The example must include at least one address with a positive score.
- The example must use a snapshot block number in the past.

Test

- The strategy should resolve in less than 10 seconds.
- The strategy should work with 500 addresses. Here is a list of addresses.

Recommended

- Add a README.md file that describes the strategy and provides an example of parameters.
- Use string ABI instead of an object.

License: MIT.

