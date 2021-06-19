CH1 SUMMARY

Blockchain - a distributed computing infrastructure where every network node
executes and records the same transactions, grouping them into blocks, and
coming to consensus on these blocks.

Ethereum - a blockchain that offers general purpose computation through smart
contracts, therefore, becoming like a "world computer".

Technical Definition: A deterministic but practically unbounded state machine,
consisting of a globally accessible singleton state and a virtual machine
that applies changes to that state.

Let's break this down. First, a state machine is a mathematical model of
computation, that can be exactly one of a (finite) number of states at any
given time. Based on the current state and some inputs, the state machine
performs some state transitions and produces outputs, and then transitions
to another state. So a state machine consists of 2 things: state and state
transitions. The state defines the current status of the machine, and various
actions that can be taken while in that state, while the transition is what
moves the state to a different "status".

Ethereum is a state machine. But it also has the specific characteristics of
being: deterministic and practically unbounded.

Deterministic means that given the same inputs, the same outputs will be 
given. Ethereum must be deterministic because you you can't have randomness 
with money. For example, if you transfer $10 from your account to Jim's, you
expect your balance to decrease by $10 and Jim's to go up by $10. And the
*exact* same event should happen every time you do this. So Ethereum is
very predictable--it has strict rules defining it's state transitions.

Practically unbounded means that there are essentially an infinite number
of possible states that the Ethereum state machine can have. In a traditional
state machine, there is only a finite number of states. However, if we think
about blockchain and its dealing with transactions and money, there is
practically an infinite number of possible states due to all the different
possible transaction combinations, money transferred, new accounts, etc.

And so we can think of Ethereum as this more or less linear state machine 
where at any given time, state is encapsulated in a block, transactions occur,
nodes execute and record these transactions, and then a new state (block)
is produced due to these state changes. And we already know how the nodes
come to consensus on the state.

Having said this, we've touched on the next part of the definition. That the
state machine consists of a "globally accessible singleton state". The
Ethereum state machine has *only* one state at any given time, and this state
is accessible by anyone, ie, anyone can view it. This is what it means to have
a public blockchain.

Finally, the other part of state machines are the state transition mechanisms.
In Ethereum, a virtual machine is responsible for applying changes to the
state and moving the machine forward. This virtual machine runs on every
node in the network, and it is what provides a standard for the state
transitions. The virtual machine is what executes all the transactions and
smart contract code (which are just transactions with data) and thus
is responsible for the state change.

And so now we have a full technical view of what Ethereum is. It is a state 
machine that has practically an infinite number of states, and it moves
to the next state via transactions, which are executed by virtual machines, 
and then recorded on the blockchain.

### Practical Definition
We can also give a practical definition:

Ethereum is a globally decentralized computing infrastructure that executes 
programs called smart contracts. It uses a blockchain to synchronize and
store the system's state changes, along with a cryptocurrency called ether
to meter and constrain execution costs.

Let's break this down. We have already established that a "decentralized
computing infrastructure" is exactly what a blockchain is. So this is akin to
saying "ethereum is a blockchain". However, this is where Ethereum stands
out. Ethereum is not just a blockchain that executes and records transactions
using a simple scripting language, like Bitcoin does.

Rather, Ethereum can execute general programs. This is an extremely powerful
capability, because now we can write programs of arbitrary complexity, and
execute them, without having to worry at all about how the underlying
blockchain, consensus mechanisms, and everything is working under the hood.
This creates a powerful layer of abstraction, since now developers are free
to innovate and create general purpose apps without having to understand
the nitpickings of a blockchain system.

A blockchain is used to synchronize and store the system's state changes.
This further reinforces the notion of a state machine. A block essentially
represents a state, and the blockchain is the actual data structure used
to maintain all the data being generated in this system.

Finally, we have a cryptocurrency, ether, which is used to "meter and
constrain execution costs". Since we are now able to develop programs of
arbitrary complexity on top of Ethereum, this opens up many possible attacks
such as DoS, and generally allows for spam and abuse of the system resources.
This, we need a disincentivizer to thwart this behave, and an economic
incentive, through the use of cryptocurrency, is a great way to do this.

### What can Ethereum be used for?
Since Ethereum has a built in Turing-complete language allowing for programs
of arbitrary complexity, this basically means that developers can build
*anything* they want. This is similar to the narrative of the web, which
allowed the development of any type of web application. But more generally,
Ethereum allows developers to build *decentralized* applications, because,
Ethereum itself is a decentralized network--anybody can join and run a node,
and it is very difficult for one party to retain a majority control over
the network.

But what can a decentralized application provide the world? First of all,
it provides high availability. In a centralized system, say youtube, all data
is generated and stored on Google servers. This serves as a central point of
failure. If those servers go down, youtube goes down with it. But in
decentralized systems, as long as one node is running, the system will keep
going on. It's hard to target a central failure point.

Ethereum also allows auditability and transparency. Because the blockchain
itself is public, any code published on it (including smart contracts), are
also totally public. Thus, instead of closed-door systems that we have with
typical companies today, all code is completely auditable and transparent,
and this hopefully will make companies more trustworthy.

Another benefit is reduction of counterparty risks. This is because in
Ethereum, we trust the "code". The code runs automatically, and thus we don't
trust middlemen and companies to handle our data and money. Instead, we rely
on the deterministic code and the decentralized network to properly handle
what we are trying to accomplish.

Finally, Ethereum is especially well suited for applications that have a
built-in economic aspect. Ethereum has a native cryptocurrency, and this makes
it easy to "program" money. This allows applications to align goals based
on an economic incentive, use tokens as a way to govern the platform, or 
make finance more decentralized. This is the power that Ethereum brings.

### Ethereum vs. Bitcoin
Ethereum shares many similarities with Bitcoin. Both have a cryptocurrency,
a P2P network, a Byzantine fault-tolerant consensus algorithm for
synchronizing state updates, and the use of cryptographic primitives such as
hashes and digital signatures to secure authenticity.

But the main way Ethereum differs is in the fact that it contains a Turing
complete programming language, which allows it to become a general purpose
blockchain. Ethereum uses a virtual machine to run and execute programs of
unbounded complexity. Bitcoin, on the other hand, has only a very simple
scripting language that evaluates to T/F based on transaction validity. This
is purposeful design, since Bitcoin was only meant to do one thing, function
as a transactional currency, a digital dollar. On the other hand, ether is a
utility currency, that helps to constrain system resources.

Thus, Ethereum can do all the things Bitcoin can do, while Bitcoin cannot do
all the things Ethereum can (at least, not as easily). This doesn't
necessarily mean Ethereum is better. But it does mean that Ethereum now
becomes a narrative, not a story. This means that Ethereum is what its
developers and users make it to be. It becomes *general-purpose*, and with
that, it can become anything that creativity throws at it.


