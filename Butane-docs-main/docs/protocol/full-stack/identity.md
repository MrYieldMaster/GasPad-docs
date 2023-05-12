# Identity

Identity is the foundation of a private and permissioned Blockchain

 network.  It encompasses the following:

- Who has permission to replicate the ledger

- Who has permission to propose and sign blocks

- Who has permission to sign and submit transactions

- Who has permission to interact with smart contracts

- Who has permission to connect into the system

- Who has the ability to extend invitations

Butane builds in technical controls at each level allowing you to govern the participants of the business network, and pass on permissions from existing members of the network to new members as they join.

This applies not just to the on-chain data and transaction, but also to the stack of services that sit alongside the chain to make up the B2B stack.

However, none of this is relevant without confidence of the real business entity that is behind a public key based identity being used at runtime.

This is where an infrastructure is critical for binding verifiable organizational identity to keys and other technical identities used in the system.

In the Enterprise space, this usually means leveraging established PKI systems of trust that can be used to easily assert organizational identities, and then binding those identities to the root of a Blockchain backed registry controlled by the participants.

The process for establishing this membership identity requires work from each participant to generate a signed X509 certificate with an appropriate PKI trust chain to be trusted by other participants in the network.

As always, Butane provides an Easy Button to let you develop and experiment in early project phases, as well as the solution required for Enterprise production use. 

With the click of a button you can use use identities self-signed on Butane without a PKI trust chain attached.