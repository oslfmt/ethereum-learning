# Wallets
A wallet is a software application that manages a user's keys and accounts.
Thus, it controls access to a user's money, and creates and signs transactions.
Wallets can also interact with contracts.

At it's simplest, a wallet is just a key-management software. That is, it
stores and manages a user's keys. Every wallet has a "key-management component"
but some wallets are broader. These wallets are called "browsers" because
they are interfaces to Ethereum dapps. However, the key component of wallets
are just containing the private keys and managing them properly.

One important point is that wallets do not actually store any ether or tokens
in them. The ether are stored in accounts, which is stored as part of the
state on the blockchain. That is, the ether are just numbers on the blockchain.
However, to actually access and transfer these funds, you must sign a
transaction with your private key, thus meaning that all control is derived
from the private key. Thus, in practice, the distinction is not important, since
the wallet ultimately is what has control over your funds, because it is what
contains your private keys. Thus, a wallet can just be thought of as a keychain,
containing pairs of public and private keys.

There are 2 main types of wallets:

1. Nondeterministic (JBOK) wallets - the keys are not related to each other,
since each is independently generated from a different random number.
2. Deterministic wallets - the keys are related to each other, since they are
all derived from a single master key (seed). All the keys can be regenerated
if one has the original seed.

## Hierarchical Deterministic Wallets (HD)
These are the most advanced deterministic wallet. Remember, a deterministic
wallet where all keys can be derived/generated from a single master key or seed.
In HD wallets, the keys are derived in a tree structure, such that a parent
key can derive a sequence of child keys, each of which can derive a sequence
of grandchild keys, and so on.

## Wallet Standards
The industry best practices include:
- Mnemonic code words (BIP-39)
- HD wallets, BIP-32
- Multipurpose HD wallet structure (BIP-43)
- Multicurrency and multiaccount wallets (BIP-44)

### Mnemonic Code Words (BIP-39)
Mnemonic code words are word sequences that encode a random number (seed)
which derives all the keys. BIP-39 defines how to create a mnemonic code and
seed. The mnemonic generates a 512-bit seed, and the seed can deterministically
derive all keys used in the HD wallet.

### HD Wallets (BIP-32) and Paths (BIP-43/44)
Keys can be extended by appending "xprv" for private keys and "xpub" for public
keys--these are called chain codes to it. The extended parent keys can then
produce child keys.

In HD wallets, you can derive child public keys from parent public keys, thus
meaning you can derive a child public key in 2 ways:
1. Directly from a child private key
2. From the parent public key

Thus, an extended public key can derive *all* of the public keys, and only the
public keys, in that branch of the HD wallet structure. This has many useful
use cases, such as storing the extended public key on a public server and then
using the public key derivation function to create a new Ethereum address for
every transaction, without ever having to store any private keys on the server.


