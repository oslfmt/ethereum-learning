## Components of Blockchain

Often time, when you ask someone "what is a blockchain?" they might spend a
few seconds in silence, and then start laying out all these things about what
blockchain is. You might hear some terms like, "P2P network", "digital
signatures", "cryptocurrency", "proof of work", and "decentralized".

This is because blockchain, really, is not just one thing, but a term that
describes a collection of things. That is, blockchain is made up of many
components, and someone coined the term because it's a flashy way to describe
this new technology. I'm going to describe all of these components of
blockchain, to hopefully give you a better understanding of what it is.

These are the components of blockchains:
- P2P network
- Consensus mechanism
- Data structures
- Incentivization scheme

Each of these components can be broken down further, but these are the main
4 components of any blockchain system. Let's break it down.

I believe it is most helpful to start off with a raw definition of what
blockchain is. Per Ethereum docs:

Blockchain is a decentralized computing infrastructure where every node in
the network executes and records the same transactions, which are grouped into
blocks.

From this definition, we can already see a few aspects of blockchain: it is
a network, or computing infrstructure, that sends transactions, or more
generally, messages between all nodes.

What does this sound like? The Internet! The Internet at its core is just a
network of devices that send messages to each other.

Let's now dive into each of the components that make up blockchain. We start
off with **data structures**. Every computing infrastructure needs data
structures in order to properly and efficiently store the data it is
processing. Let's forget the network for now, and think about what it would
be like to build a digital currency from the ground up.

Assume, we have a group of friends who want to implement a digital currency.
Assume also that we only have one computer, or node. If all friends trust
each other, then implementing a digital currency is rather simple. On the one
computer that we own, we can implement a few data structures in our system.
These structures would store things like the balances of everyone's accounts,
a history of transactions, etc. But this is severely limited because everyone
would have to use that one computer.

And so now we say, everyone in the group has a device that can send
transactions of this digital currency. Now, we have to add in the **P2P
Network**, since we have multiple computers. This network serves to connect
all the participants, and propagate the transactions to the central computer
that is storing all the balances and transaction history, essentially acting
as a central database.

And so now we have a fully functioning system. With our data structures and
network, we can scale up, and add many users to our system. The central 
computer now has to maintain trust. It hasn't messed or tampered with anyone's
funds yet, so people begin to trust the central computer. However, this poses
a big issue, and that is the problem of centralization.

The problem blockchain seeks to solve, is how to get rid of this central power,
how to decentralize the system. Instead of having a central entity be the sole
owner of the ledger of all balances and transactions, how about we have every
single person in the network maintain this ledger. That way, we don't have
to trust and rely on a central institution. The problem now becomes, how do
we get every single ledger to agree with each other?

And this is where the other two components come in--a **consensus mechanism**
and **incentivization scheme**. A consensus mechanism is a protocol to get
the entire system to come to consensus, or agreement, on something. In the
case of blockchains, it would be coming to agreement on the state of a ledger.

Consensus mechanisms aren't a new revelation in computer science. They are
a critical component to distributed systems, which is essentially what a
blockchain is. However, blockchains operate in a fully open environment. Not 
only are there nodes that will fail or shut down, they could be down right
malicious as well.

Now, there are a few things that we must come to consensus on. We have to
agree on what constitutes a transaction, what makes for a valid state
transition, and an algorithm to force all nodes to cooperate in the
enforcement of consensus rules. That is, we can define rules for what a
transaction is, what a state change is, but these rules are meaningless if no
one plays by them.

Traditionally, consensus protocols such as Paxos and Raft use voting based
consensus. In each round, or new state change of the system, all the nodes
submit a vote to vote on the valid state, and this becomes the new state.
This works well for a closed system, where you can easily enforce all nodes
to play by these rules, since you own all these nodes. But in a blockchain
system, you cannot force all nodes to do that.

However, you can incentivize them! And this is where the cryptocurrency comes
in. The crypto serves as a native mechanism, an economic incentive, to get
nodes to play by the rules and do the right thing, or else they miss out on
the opportunity of making money. And so by introducing an **incentivization
scheme** you can effectively guide the system to play by the rules. Of course,
nodes can choose not to, but that usually means they are missing out on
profits, or even losing money.

To sum up, all the components of an open, public blockchain are:
- P2P Network - connects nodes and propagates transactions and blocks between
nodes. Usually based on a standard "gossip" protocol
- Messages - in blockchain systems, these take the form of transactions.
Transactions allow for state transitions.
- Consensus rules - these rules define what constitutes a transaction (to,
from, amount, data), as well as what makes a valid state transition (block
parameters, PoW solution, root hash, etc.)
- State machine - processes transactions according to consensus rules. This
piece of software ensures only valid transactions and state changes occur.
This is the actual mechanism that processes the transactions and produces
state changes.
- Blockchain data structure - this is the shared ledger that stores all the
account balances, transaction history, ie, the state of the system. It is
a chain of cryptographically linked blocks.
- Consensus algorithm - this protocol (PoW, PoS) acts to force participants
to cooperate in enforcing the consensus rules, and thus agree on a valid
blockchain history and state.
- Incentivization scheme - the scheme that economically secures the state
machine in an open, decentralized environment.

All of the above components are combined and implemented in an open source
software implementation, called a client.

In Bitcoin, the components of the blockchain, are, more specifically:
- P2P Network - Bitcoin network
- Messages - Bitcoin uses UTXO model for transactions
- Consensus rules - a valid transaction is one that, after running the
transaction script, it ultimately evaluates to true. More specifically, the
transaction spends from an "unspent transaction output", specifies the correct
recipient address, and then provides the correct digital signature verifying
ownership of the public key to that address.
- State machine - Bitcoin clients process transactions using a simple stack
based language, called Bitcoin script. All transactions are processed this
way, and there is only one type of transaction.
- Blockchain - Bitcoin blocks have a 1MB size, filled with transactions.
Additionally, there is a block header, which has lots of metadata information,
including the block hash, nonce, PoW solution, and previous block hash. The
previous block hash is what links the current block to the previous one, and
thus makes the blockchain tamper evident and resistant.
- Consensus Algorithm - Bitcoin uses the PoW algorithm. Essentially, anyone
can group together some transactions into a block, and all transactions could
totally be valid, and so we have a ton of possible valid blocks, when we can
only have one block (this is because having multiple blocks essentially, means
many different histories, which means many double spends, and just leads to
an invalid chain). Since we have many possible valid blocks, we could simply
say that whichever block is proposed first in the network is the valid block.

However, this doesn't work because simply creating a 1MB block is incredibly
fast, and so everyone will broadcast their blocks at roughly the same time,
and the blocks that other nodes receive will be dependent on network effects.
And so we get a system where we have a bunch of nodes that have accepted
different blocks, and we get many forks in the blockchain, leading to a
divided, and thus less secure, ecosystem.

So how about we have everyone vote on what they think should be the next
block? However, the problem with this is sybil attacks. Remember, the node
whose block gets accepted gets a block reward. And so by counting votes, each
node could create an unbounded number of fake or sybil identities, which
appear different, but in reality are all controlled by one person. This leads
to a similarly chaotic system.

The solution comes in, instead of 1-person-1-vote, we have 1-computer-1-vote.
That is, we limit voting to a scarce resource, computational power in this
case. In PoW, we have computers do work. This work is essentially finding a
hash that has a certain property (10 zeros in the first 10 digits). This takes
a lot of time, thus solving the first network propagation problem. Secondly,
creating sybil identities is now hard. To create another node, you have to
expend more computational power and electricity. Thus, PoW creates a
competition where all nodes are competing to propose the next block, in order
to get that block reward.

- Incentivization scheme - Bitcoin uses PoW, block rewards, and transaction
fees. Nodes are incentivized to only include valid transactions, because if
not, then it is unlikely their block will be accepted, and they will have
wasted all that computational power. Essentially, these economic incentives
work to secure the system.

- Software client implementation - Bitcoin Core has developed the bitcoind
client, which implements all of the above things.

## Ethereum Components
Now let's take a look at the specific components of Ethereum. Since Ethereum
is general purpose, this means that not only does it track the state of
currency ownership, Ethereum tracks state transitions of a general-purpose
data store. Ethereum can store both code and data, and load code into its
state machine (EVM) to run it, producing a new state. In this way, Ethereum
acts as a general-purpose computer. However, Ethereum is also distributed
globally and is a computer that operates under consensus.

- P2P Network - Ethereum runs on the Ethereum mainnet, which is addressable
on TCP port 30303, and runs a protocol called DEVp2p.
- Consensus rules - what constitutes a valid transaction and state transition
is defined in the reference specification, the Yellow Paper
- Transactions - network messages that include things like a sender, recipient,
value, and data payload
- State Machine - Ethereum has a more complicated state machine than Bitcoin.
The state machine is the EVM, which is a stack-based VM that executes bytecode.
- Data Structures - Ethereum's state is stored locally on each node as a
database (LevelDB), which contains transactions and state in a serialized
hashed data structure known as a Merkle Patricia Tree
- Consensus Algorithm - Ethereum uses Nakamoto consensus, but will switch
to a PoS weighted voting system called Casper.
- Economic Security - Ethereum used to use Ethash, but will move to a PoS.
- Clients - Ethereum has a reference specification, which means many different
client can be implemented to run the Ethereum protocol.


