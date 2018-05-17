# Important Points for Hyperledger Fabric and Hyperledger Composer

  - Hyperledger Fabric's modular architecture maximizes the confidentiality, resilience, and flexibility of blockchain solutions.


## Transaction lifecycle in v1.0 of Hyperledger Fabric

1) The transaction proposal is submitted by an application to an endorsing peer. 
2) The Endorsement policies outline how many and/or what combination of endorsers are required to sign a proposal. The endorser executes the chaincode to simulate the proposal in the network peer, creating a read/write set. 
3) Then the endorsing peers send back the signed proposal responses (endorsements) to the application. 
4) The application submits the transactions and signatures to the ordering service, which 
5) creates a batch, or block, of transactions and delivers them to committing peers. 
6) When a committing peer receives a batch of transactions, for each transaction it 
7) validates that the endorsement policy was met and checks in the read/write sets to detect conflicting transactions. If both checks pass, the block is committed to the ledger, and the state updates for each transaction are reflected in the state database.

![blockchain_basic_network](https://github.com/srikanthg-techie/hlf-composer/blob/master/images/Transaction%20Lifecycle.png)


## Other Info
Orderer node - Consensus
Channel - Privacy and Confidentiality
Membership Service Provider - Identity



The Linux Foundation founded Hyperledger in 2015 to advance cross-industry blockchain technologies.

Hyperledger Fabric is one of the blockchain projects within Hyperledger. Like other blockchain technologies, it has a ledger, uses smart contracts, and is a system by which participants manage their transactions.

Where Hyperledger Fabric breaks from some other blockchain systems is that it is private and permissioned. 
The members of a Hyperledger Fabric network enroll through a trusted Membership Service Provider (MSP).

Hyperledger Fabric also offers several pluggable options. Ledger data can be stored in multiple formats, consensus mechanisms can be swapped in and out, and different MSPs are supported.

Shared Ledger:
Hyperledger Fabric has a ledger subsystem comprising two components: the world state and the transaction log. Each participant has a copy of the ledger to every Hyperledger Fabric network they belong to.

The world state component describes the state of the ledger at a given point in time. It’s the database of the ledger. The transaction log component records all transactions which have resulted in the current value of the world state; it’s the update history for the world state. The ledger, then, is a combination of the world state database and the transaction log history.

The ledger has a replaceable data store for the world state. By default, this is a LevelDB key-value store database. The transaction log does not need to be pluggable. It simply records the before and after values of the ledger database being used by the blockchain network.


Smart Contracts:
Hyperledger Fabric smart contracts are written in chaincode and are invoked by an application external to the blockchain when that application needs to interact with the ledger. In most cases, chaincode interacts only with the database component of the ledger, the world state (querying it, for example), and not the transaction log.


Privacy:
Depending on the needs of a network, participants in a Business-to-Business (B2B) network might be extremely sensitive about how much information they share. For other networks, privacy will not be a top concern.

Hyperledger Fabric supports networks where privacy (using channels) is a key operational requirement as well as networks that are comparatively open.


Consensus:
Transactions must be written to the ledger in the order in which they occur, even though they might be between different sets of participants within the network. For this to happen, the order of transactions must be established and a method for rejecting bad transactions that have been inserted into the ledger in error (or maliciously) must be put into place.

PBFT (Practical Byzantine Fault Tolerance) can provide a mechanism for file replicas to communicate with each other to keep each copy consistent, even in the event of corruption.


Hyperledger Fabric Functionalities:
Identity management:
To enable permissioned networks, Hyperledger Fabric provides a membership identity service that manages user IDs and authenticates all participants on the network. Access control lists can be used to provide additional layers of permission through authorization of specific network operations. For example, a specific user ID could be permitted to invoke a chaincode application, but blocked from deploying new chaincode.

Privacy and confidentiality:
Hyperledger Fabric enables competing business interests, and any groups that require private, confidential transactions, to coexist on the same permissioned network. Private channels are restricted messaging paths that can be used to provide transaction privacy and confidentiality for specific subsets of network members.

Efficient processing:
Hyperledger Fabric assigns network roles by node type. To provide concurrency and parallelism to the network, transaction execution is separated from transaction ordering and commitment. Executing transactions prior to ordering them enables each peer node to process multiple transactions simultaneously. This concurrent execution increases processing efficiency on each peer and accelerates delivery of transactions to the ordering service.

Modular design:
Hyperledger Fabric implements a modular architecture to provide functional choice to network designers. Specific algorithms for identity, ordering (consensus) and encryption, for example, can be plugged in to any Hyperledger Fabric network.

















