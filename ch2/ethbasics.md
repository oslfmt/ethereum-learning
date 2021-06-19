Wallet - software application that helps users manage their Ethereum account
       - holds keys
       - broadcasts transactions to network on your behalf

EVM: the emulated computer that runs all smart contract code. The EVM is
"a global singleton", meaning that it operates as if it were a global,
single-instance computer running everywhere.

Each node on the network runs a local copy of the EVM to validate contract
execution, while the blockchain itself stores the state changes of the
world computer as it processes transactions and smart contracts.

Account Types
EOA - externally owned account. This is an account that has a private key,
and is controlled by a user. The private key gives the user access to funds
in the account, or contracts.

Contract account - this account has smart contract code, which EOAs cannot
possess. A contract account also does not have a private key, meaning that
no one really owns the contract. Rather, it is controlled by the logic of the
smart contract code that resides in it. The code itself is what is recorded
on the Ethereum blockchain at the contract account's creation and executed
by the EVM.

- Both EOAs and contracts have addresses
- contract accounts can also send and receive ether, just like EOAs
- the way the code in a contract can run is by sending a transaction, with
the transaction destination being the contract address, and the transaction
data payload as the input (indicating functions to call, parameters to those
functions, etc).

Since a contract doesn't have a private key, it thus cannot initiate a
transaction--only EOAs can do this. However, contracts can react to
transactions by calling other contracts.

Creating a Contract
1. Write the contract code, in a language like Solidity
2. A solidity compiler translates the Solidity contract source code into EVM
bytecode.
3. Register (upload) the contract onto the Ethereum blockchain. This entails
creating a transaction with destination address as 0x0, the zero address.
This tells the blockchain that this is a special transaction, ie, it is a
contract registration.
4. Once the transaction is mined, the contract account is created at some
address, and the smart contract code just written lies there.

Interacting with a Contract
1. Now that the contract is registered on the blockchain, any transactions
sent to the contract address causes the contract code to run in the EVM, with
the transaction data as inputs.
2. Transactions can contain ether, data, or both. Any ether is simply sent
to the contract balance. Transaction data specifies which function to call,
as well as the parameters to that function.



