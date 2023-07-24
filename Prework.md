# Notes
Notes I'm making while going through the prework material, mostly the first two chapters of Ethereumbook
## What is Ethereum
Ethereum is a deterministic but practically unbounded state machine, consisting of a globally accessible singleton state and a virtual machine that applies changes to that state.

### Similarities with Bitcoin
Ethereum shares many common elements with other open blockchains: a peer-to-peer network connecting participants, a Byzantine fault–tolerant consensus algorithm for synchronization of state updates (a proof-of-work blockchain), the use of cryptographic primitives such as digital signatures and hashes, and a digital currency (ether).

### Differences between Ethereum and Bitcoin
* Ethereum’s purpose is not primarily to be a digital currency payment network. Ether is only intended as a utility currency to pay for use of the Ethereum platform as the world computer.  
* Bitcoin has a very limited scripting language - constrained to simple true/false evaluation of spending conditions
* Ethereum is designed to be a general-purpose programmable blockchain that runs a virtual machine capable of executing code of arbitrary and unbounded complexity. Ethereum’s language is Turing complete, meaning that Ethereum can straightforwardly function as a general-purpose computer.

### Components of a Blockchain
1. A peer-to-peer (P2P) network connecting participants, executing transactions and storing blocks of verified txns, based on a standardized gossip protocol
2. Messages, in the form of transactions, representing state transitions
3. A set of consensus rules, governing what constitutes a transaction and what makes for a valid state transition
4. A state machine that processes transactions according to the consensus rules
5. A chain of cryptographically secured blocks that acts as a journal of all the verified and accepted state transitions
6. A consensus algorithm that decentralizes control over the blockchain, by forcing participants to cooperate in the enforcement of the consensus rules
7. A game-theoretically sound incentivization scheme (e.g., proof-of-work costs plus block rewards) to economically secure the state machine in an open environment
8. One or more open source software implementations of the above ("clients")

All or most of these components are usually combined in a single software client. For example, in Bitcoin, the reference implementation is developed by the Bitcoin Core open source project and implemented as the bitcoind client. In Ethereum, rather than a reference implementation there is a reference specification, a mathematical description of the system in the Yellow Paper (https://ethereum.github.io/yellowpaper/paper.pdf)

### Idea behind Ethreum 
The idea was that by using a general-purpose blockchain like Ethereum, a developer could program their particular application without having to implement the underlying mechanisms of peer-to-peer networks, blockchains, consensus algorithms, etc. The Ethereum platform was designed to abstract these details and provide a deterministic and secure programming environment for decentralized blockchain applications.

### Architecture of Bitcoin
Bitcoin’s blockchain, tracks the state of units of bitcoin and their ownership. You can think of Bitcoin as a distributed consensus state machine, where transactions cause a global state transition, altering the ownership of coins. The state transitions are constrained by the rules of consensus, allowing all participants to (eventually) converge on a common (consensus) state of the system, after several blocks are mined.

### Architecture of Ethereum
* Ethereum is a distributed state machine. But instead of tracking only the state of currency ownership, Ethereum tracks the state transitions of a general-purpose data store, i.e., a store that can hold any data expressible as a key–value tuple. 
* A key–value data store holds arbitrary values, each referenced by some key; for example, the value "Mastering Ethereum" referenced by the key "Book Title". In some ways, this serves the same purpose as the data storage model of Random Access Memory (RAM) used by most general-purpose computers.
* Ethereum has memory that stores both code and data, and it uses the Ethereum blockchain to track how this memory changes over time. Like a general-purpose stored-program computer, Ethereum can load code into its state machine and run that code, storing the resulting state changes in its blockchain. 
* Two of the critical differences from most general-purpose computers are that Ethereum state changes are governed by the rules of consensus and the state is distributed globally. Ethereum answers the question: "What if we could track any arbitrary state and program the state machine to create a world-wide computer operating under consensus?"

### Components in Ethereum
1. P2P network : Ethereum runs on the Ethereum main network, which is addressable on TCP port 30303, and runs a protocol called ÐΞVp2p.
2. Consensus rules - check Yellow Paper for details
3. Transactions : Ethereum transactions are network messages that include (among other things) a sender, recipient, value, and data payload.
4. State Machine - Ethereum state transitions are processed by the Ethereum Virtual Machine (EVM), a stack-based virtual machine that executes bytecode (machine-language instructions). EVM programs, called "smart contracts," are written in high-level languages (e.g., Solidity) and compiled to bytecode for execution on the EVM.
5. Data Structures - Ethereum’s state is stored locally on each node as a database (usually Google’s LevelDB), which contains the transactions and system state in a serialized hashed data structure called a Merkle Patricia Tree.
6. Consensus algorithm - #todo check this, coz I think its now POS
7. Clients : Ethereum has several interoperable implementations of the client software, the most prominent of which are Go-Ethereum (Geth) and Parity.
8. Further Resources - https://github.com/ethereumbook/ethereumbook/blob/develop/01what-is.asciidoc#further-reading
## Ethereum Basics

* Ethereum’s currency unit is called ether, identified also as "ETH" or with the symbols Ξ. One ether is 1 quintillion wei (1 * 1018 or 1,000,000,000,000,000,000).
* Wallet - A software application that helps you manage your Ethereum account. e.g MetaMask, Jaxx, MyEtherWallet, Emerald Wallet
* Control and Responsibility 
  * Each user of Ethereum can and should control their own private keys, which are used to access funds and smart contracts. The combination of funds + smart contracts is refererred to as a wallet/account. One private key equals one "account.
  * Responsibility - If you lose your private keys, you lose access to your funds and contracts. Never store your private key in plain form, especially digitally. 
  * Private keys can be stored in an encrypted form, as a digital "keystore" file. Being encrypted, they need a password to unlock.