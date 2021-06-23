# Ethereum Clients
An Ethereum client is a software application that implements the Ethereum
specification and communicates over the P2P network with other clients.
There are many different client implementations, and they are all interoperable
since they all conform to the reference specification. All clients "speak"
the same protocol and operate on the same rules.

Full node - downloads the entire blockchain and validates transactions and
blocks
Remote client - does not store a local copy of the blockchain or validate
blocks and transactions. Offers the functionality of a wallet (creates and
broadcasts transactions). Remote clients can connect to your own full node,
a public blockchain, testnet, or local blockchain.

Remote clients differ from wallets in that they also offer an API (like web3.js
), in addition to the transaction functionality of a wallet.

Remote clients also differ from light clients. Light clients validate block
headers and use Merkle proofs to validate the inclusion of transactions in the
blockchain they they specifically are interested in. This gives them a level
of security similar to a full node. Remote clients do not validate block
headers or transactions, and you trust a full client to get access to a
blockchain.

### Full Node Advantages
- Support the security and resilience of the Ethereum blockchain
- Authoritatively validate all transactions
- Interact with contracts directly, not through intermediary
- Deploy contracts directly, without an intermediary
- Can query the blockchain state while offline
- Can query blockchain without letting a 3rd party know the info you're reading

### Full Node Disadvantages
- Requires a hardware, bandwidth, and electricity costs
- May require lots of time to fully sync
- Must be regularly maintained, upgraded, and online to remain in sync

## Remote Ethereum Clients
These clients do not store the full blockchain, and offer the ability to:
- Manage private keys and addresses in a wallet
- Create, sign, and broadcast transactions
- Interact with smart contracts
- Browse and interact with Dapps
- Offer links to external services such as block explorers
- Convert ether units
- Inject a web3 instance into the web browser as a JS object
- Use a web3 instance provided/injected into browser by another client
- Access RPC services on a local or remote Ethereum node


