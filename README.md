# Hyperledger Fabric and Composer - The Collected Documentation from Different Sources

Note: This document covers Hyperledger Fabric 1.1 and Hyperledger Composer 0.9.x


## Hyperledger Fabric : 

Detailed information on Hyperledger Fabric.


### What is Hyperledger Fabric?

Hyperledger Fabric is a platform for distributed ledger solutions underpinned by a modular architecture delivering high degrees of confidentiality, resiliency, flexibility and scalability.

**Confidentiality** :
The ability to control access to sensitive data. It enables life changing applications of the blockchain technology such as medical records management, real-time settlement of financial transactions and personal identity management.

* *The business side of confidentiality* :
  - For each transaction supported by the smart contract, which participants should be able to see all, a subset or none of the transaction data including who submitted?
  - Is there a participant with the role of regulator? If so, what data needs to be accessed by the regulator?
  - Is your business network design flexible enough? Confidentiality rules could change in the future as the business network grows by adding new participants with different confidentiality needs.

* *The technical side of confidentiality* :
  - The data at-rest from the ledger or the state database should rely on an encrypted highly available file system. Hyperledger Fabric can secure data in-transit by enabling two-way Transport Layer Security (TLS).
  - Next stop is to leverage Hyperledger Fabric Attribute-Based Access Control. This means that access control decisions regarding which user can execute which transactions, are based upon the user’s identity attributes. For example, the “changeMedicalRecord” operation exposed by a smart contract is only available to the record owner.
  - Next is to encrypt sensitive data using the Hyperledger Fabric encryption library. For example, a smart contract transaction can encrypt a person’s Social Security number when its written to the ledger. Only key participants in the network (for example, the regulator) should have access to the decryption keys. Note that the management of the encryption/decryption keys should be done outside HL Fabric.
  - Up to now, all organizations in the business network will receive all transaction data, although a subset may be encrypted per the previous point. What about not sending the sensitive data altogether to those organizations that don’t need to have it in the first place. This can be done by leveraging a Hyperledger Fabric feature called “Private channel data”. Here, the sensitive data is only shared with those organizations that need to have access to it. For example, all organizations in the network can see that a person has health insurance, but the insurance coverage details is only available to the medical provider organizations in the network. Note that “Private channel data” is an experimental feature in HL Fabric v1.1
  - So far, all organizations in the business network join the same common distributed ledger. The next level of confidentiality supported by Hyperledger Fabric is about having separate ledgers or “channels”. In Hyperledger Fabric, each distributed ledger in the network lives only within the context of a channel. Therefore, total data confidentiality across organizations that don’t need to share any data can be achieved by assigning these organizations to separate channels. For example, a major hotel chain could define two channels: one channel where the hotel chain sub-brands can publish empty rooms and another channel where these empty rooms are auctioned across travel agencies. In this example, there is total isolation between the two channels except that the major hotel chain as the founder of this business network can connect and transact in both.


### What is a Blockchain?

* **A Distributed Ledger**

  - At the heart of a blockchain network is a distributed ledger that records all the transactions that take place on the network.
  - A blockchain ledger is often described as decentralized because it is replicated across many network participants, each of whom collaborate in its maintenance.
 - In addition to being decentralized and collaborative, the information recorded to a blockchain is append-only, using cryptographic techniques that guarantee that once a transaction has been added to the ledger it cannot be modified. This property of immutability makes it simple to determine the provenance of information because participants can be sure information has not been changed after the fact. It’s why blockchains are sometimes described as systems of proof.
![blockchain_basic_network](https://user-images.githubusercontent.com/20517136/40042858-5eef2050-5840-11e8-9672-b536f331b15e.png)

* **Smart Contract**
  - To support the consistent update of information – and to enable a whole host of ledger functions (transacting, querying, etc) – a blockchain network uses smart contracts to provide controlled access to the ledger.
![blockchain_basic_network](https://hyperledger-fabric.readthedocs.io/en/release-1.1/_images/Smart_Contract.png)
  - Smart contracts are not only a key mechanism for encapsulating information and keeping it simple across the network, they can also be written to allow participants to execute certain aspects of transactions automatically.
  - A smart contract can, for example, be written to stipulate the cost of shipping an item that changes depending on when it arrives. With the terms agreed to by both parties and written to the ledger, the appropriate funds change hands automatically when the item is received.


* **Consensus**
  - The process of keeping the ledger transactions synchronized across the network – to ensure that ledgers update only when transactions are approved by the appropriate participants, and that when ledgers do update, they update with the same transactions in the same order – is called consensus.
![blockchain_basic_network](https://hyperledger-fabric.readthedocs.io/en/release-1.1/_images/consensus.png)





#### References:
https://hyperledger-fabric.readthedocs.io/en/release-1.1/blockchain.html
https://www.ibm.com/blogs/blockchain/2018/04/hyperledger-fabric-enables-confidentiality-in-blockchain-for-business/
