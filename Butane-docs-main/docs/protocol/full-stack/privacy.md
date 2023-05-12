

# Privacy

Just because a Blockchain is private & permissioned, does not mean that the parties involved wish to make all of their data and transactions visible to all other participants within the business network. There are many reasons why data might need to be kept private.

## Competition

Blockchain based business networks often foster coopetition. Enterprises collaborate in the business network for a common benefit, while actively competing with each other. These are some of the healthiest and most dynamic ecosystems. However, knowledge of details of a business transaction/trade, or the simple fact that a trade happened between a set of parties in the business network, might provide data that other parties could use to gain a competitive advantage.

## Data Privacy

Some data is simply too sensitive to include on an immutable shared ledger. Consider the example of Sensitive Personal Information - this is often governed by strong data protection legislation such as GDPR, including controls that mean it must be deleted upon request from the owner of that data. Even if their data itself is not held on-chain there might be the potential for metadata leakage breaching privacy. 

Consider tracing drivers' license information on-chain - even if the identity is not widely available, you might be able to infer from direct knowledge of one citation a link to the token that represents a person on-chain. From there you can see that person's full history.

## Privacy Solutions

Practical solutions for privacy are available today, and there are maturing solutions that are gaining traction and evolving to become practical for Enterprise use.

## Proof-only Solutions and HD Wallets

In cases where all the material actions for a transaction are coordinated off-chain (see the next topic on off-chain comms),

 it might only be required to put a record of agreement on-chain. A signature from each party involved that agreement has been reached. This can take the form of a simple proof readable only to the other parties involved.

Sign some data that designates the agreement using your private key
Encrypt that data with the public key of each party that needs to read the proof

Put each of those encrypted proofs on-chain

Once all parties have submitted their proofs on-chain, the agreement is immutably recorded

However, in order to avoid leaking information about who is involved in a transaction you must first mask the identity that is submitting the transaction to the chain. 

It is possible in some cases to simply generate a completely random address to sign the Blockchain transaction. 

However, that does not allow for permissioning of who can submit signatures to the contract, or traceability back to who submitted the transaction.

 As such, a Hierarchically Deterministic (HD) Wallet is commonly used to generate a single-use Ethereum address that the owner can prove is their own if asked.

## Private Transaction Managers & Enclaves

One of the most popular options to make transactions and data visible only to a subset of the participants, is to use a Private Transaction Manager such as Tessera from Quorum (the successor to the original Constellation project in this space) or Orion from PegaSysEng.

These work by sending off-chain point-to-point encrypted communications to select parties that are allowed to view the full input data for the transactions. 

These select parties can process the full transaction, and update their state to include the full results. Other parties in the network maintain a proof that the data was sent, a hash of the payload and the address of the sender, but cannot execute the transaction as they never receive the encrypted payload.