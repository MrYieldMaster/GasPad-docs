# Decentralized Applications

If you've found Butane, then you've almost certainly heard of a “DApp” – or Decentralized Application.

These concepts almost always tie back to ownership, and identity. Here, tokenization is the built-in construct of a Blockchain that pins whole or fractional ownership of something real or digital that exists off-chain, to an on-chain representation.

 You can extend tokens with custom smart contract logic and on-chain state. Then pin your on-chain state to rich off-chain data storage with a simple hash. 
 
 In some cases value is then attributed to tokens, and tokens of different types can be swapped to designate change of ownership of the asset, with enforced rules.

## Proofs, Keys and Identity

Signing a payload like a transaction, or any other cryptographic proof, allows you to state some data to another party with certainty that it came from you. 

The digital signature delivers invaluable non-repudiation, as at any point in the future the holder can irrefutably prove that you as the private key owner stated that data.


Sometimes proofs are stated openly, and written to the shared ledger for everyone in the business network to see.

Other times the proofs are masked so that only those holding other secrets are able to view them.

In all cases, the keys used to sign those proofs are sensitive. Whether used once from a never ending deterministic sequence of keys, like a hierarchically deterministic (HD) wallet, or bound to an organizational identity where the public key is shared in an on-chain registry, the lifecycle and management of keys is a significant consideration in any Blockchain based business network.


Putting the Right Data on the Shared Ledger
Maybe the most important thing to recognize when building a decentralized application, is that the chain is not intended to be treated as a traditional database.

Data written to the chain should be considered immutable
It is practically impossible to purge data from the ledger in a Blockchain, so any sensitive personal data or other data that might be subject to requirements to remove it at a later date is unsuitable for storage on-chain 

(without encryption enabling cryptographic deletion)

All data ever written remains available


The storage collects over time, so writing large amounts of data has a cumulative impact on storage requirements over time. For this reason storage of large payloads is not practical.

The transaction ledger is maintained via distributed consensus
With byzantine fault tolerant consensus algorithms, coordination and proofs that occur as blocks are mined are expensive, and it takes significantly longer than the transaction commit times of a locally replicated SQL or no-SQL database.

## Finality is dependent on consensus

Different consensus algorithms have different approaches to when transaction state becomes immutable. Unlike the eventual consistency and optimistic concurrency locking of traditional databases, the time to finality can be long.

 For some consensus algorithms, forks in the chain can exist for significant periods of time before sufficient agreement exists in the network for the transaction order to be considered permanent.


So DApp design is about determining the right amount of data, often including proofs, to be captured in the shared ledger and to be controlled via Smart Contract logic.

 Then coordinating the updates to that data through rich user experiences, core-system integration within each participant of the business network, and off-chain communications between participants to exchange state and data.