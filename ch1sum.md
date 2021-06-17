CH1 SUMMARY

Blockchain - a distributed computing infrastructure where every network node
executes and records the same transactions, grouping them into blocks, and
coming to consensus on these blocks.

Ethereum - a blockchain that offers general purpose computation through smart
contracts

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
moves the state to a different state.

Ethereum is a state machine. But is is also deterministic and practically
unbounded.

Deterministic means that given the same inputs, the same outputs will be 
given. Ethereum must be deterministic because you have to have the same 
outputs given inputs, you can't have randomness with money. So Ethereum is
very predictable--it has strict rules defining it's state transitions.

Practically unbounded means that their are essentially an infinite number
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
is accessible by anyone, ie, anyone can view it.

Finally, the other part of state machines are the state transition mechanisms.
In Ethereum, a virtual machine is responsible for applying changes to the
state and moving the machine forward. This virtual machine runs on every
node in the network, and it is what provides a standard for the state
transitions. The virtual machine is what executes all the transactions and
smart contract code (which are also just transaction with data) and thus
is responsible for the state change.

And so know we have a full technical view of what Ethereum is. It is a state 
machine that has practically an infinite number of states, and it moves
to the next state via transactions, which are executed by virtual machines, 
and then recorded on the blockchain.

### Practical Definition
Ethereum is a globally decentralized computing infrastructure that executes 
programs called smart contracts. It uses a blockchain to synchronize and
store the system's state changes, along with a cryptocurrency called ether
to meter and constrain execution costs.
