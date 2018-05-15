# Hyperledger Fabric and Composer - The Collected Documentation from Different Sources

Note: This document covers Hyperledger Fabric 1.1 and Hyperledger Composer 0.9.x


## Hyperledger Fabric : 

Detailed information on Hyperledger Fabric.


### What is Hyperledger Fabric?

Hyperledger Fabric is a platform for distributed ledger solutions underpinned by a modular architecture delivering high degrees of confidentiality, resiliency, flexibility and scalability.

* **Confidentiality** :
The ability to control access to sensitive data. It enables life changing applications of the blockchain technology such as medical records management, real-time settlement of financial transactions and personal identity management.

* *The business side of confidentiality* :
Let’s be clear, these business concepts apply not only to Hyperledger Fabric but to any underlying blockchain platform or technology. From a business point of view, confidentiality is a key feature. Participants in a Business-to-Business (B2B) network might be extremely sensitive about how much information they share. We should design the blockchain business network in a way that supports the confidentiality requirements of the use case at hand. Which means that we need to understand at a very deep level which network participant have access to what data under which conditions. These are a few key points for you to keep in mind during the business network design:

For each transaction supported by the smart contract, which participants should be able to see all, a subset or none of the transaction data including who submitted?
Is there a participant with the role of regulator? If so, what data needs to be accessed by the regulator?
Is your business network design flexible enough? Confidentiality rules could change in the future as the business network grows by adding new participants with different confidentiality needs.


* *The technical side of confidentiality* :
On the technical side, let’s see what features in Hyperledger Fabric support confidentiality. For the sake of completeness, some recommendations related to data security are also included here. The following list shows an increasing level of sophistication around confidentiality control and data security:

Let’s start with the basics. The data at-rest from the ledger or the state database should rely on an encrypted highly available file system. Hyperledger Fabric can secure data in-transit by enabling two-way Transport Layer Security (TLS).
Next stop is to leverage Hyperledger Fabric Attribute-Based Access Control. This means that access control decisions regarding which user can execute which transactions, are based upon the user’s identity attributes. For example, the “changeMedicalRecord” operation exposed by a smart contract is only available to the record owner.
Next is to encrypt sensitive data using the Hyperledger Fabric encryption library. For example, a smart contract transaction can encrypt a person’s Social Security number when its written to the ledger. Only key participants in the network (for example, the regulator) should have access to the decryption keys. Note that the management of the encryption/decryption keys should be done outside HL Fabric.
Up to now, all organizations in the business network will receive all transaction data, although a subset may be encrypted per the previous point. What about not sending the sensitive data altogether to those organizations that don’t need to have it in the first place. This can be done by leveraging a Hyperledger Fabric feature called “Private channel data”. Here, the sensitive data is only shared with those organizations that need to have access to it. For example, all organizations in the network can see that a person has health insurance, but the insurance coverage details is only available to the medical provider organizations in the network. Note that “Private channel data” is an experimental feature in HL Fabric v1.1
So far, all organizations in the business network join the same common distributed ledger. The next level of confidentiality supported by Hyperledger Fabric is about having separate ledgers or “channels”. In Hyperledger Fabric, each distributed ledger in the network lives only within the context of a channel. Therefore, total data confidentiality across organizations that don’t need to share any data can be achieved by assigning these organizations to separate channels. For example, a major hotel chain could define two channels: one channel where the hotel chain sub-brands can publish empty rooms and another channel where these empty rooms are auctioned across travel agencies. In this example, there is total isolation between the two channels except that the major hotel chain as the founder of this business network can connect and transact in both.


### What is a Blockchain?

**A Distributed Ledger**



![blockchain_basic_network](https://user-images.githubusercontent.com/20517136/40042858-5eef2050-5840-11e8-9672-b536f331b15e.png)











#### References:
https://hyperledger-fabric.readthedocs.io/en/release-1.1/blockchain.html
https://www.ibm.com/blogs/blockchain/2018/04/hyperledger-fabric-enables-confidentiality-in-blockchain-for-business/
