---
sidebar_position: 7
---

# Butane-Name-Service

BNS has similar goals to DNS, the Internet’s Domain Name Service,

 but has significantly different architecture due to the capabilities and constraints provided by the Ethereum blockchain.
 
  Like DNS, BNS operates on a system of dot-separated hierarchical names called domains, with the owner of a domain having full control over subdomains.

Top-level domains, like ‘.bbc’ and ‘.test’, are owned by smart contracts called registrars, 

which specify rules governing the allocation of their subdomains. Anyone may, by following the rules imposed by these registrar contracts, obtain ownership of a domain for their own use. ENS also supports importing in DNS names already owned by the user for use on ENS.

Because of the hierarchal nature of ENS, anyone who owns a domain at any level may configure subdomains
 - for themselves or others
  - as desired. For instance, if Alice owns 'alice.bbc',
- she can create 'pay.alice.bbc' and configure it as she wishes.
BNS is deployed on the Butane main network and on several test networks. 

If you use a library such as the ensjs Javascript library, or an end-user application, it will automatically detect the network you are interacting with and use the BNS deployment on that network.

Similiar to [ENS](https://docs.ens.domains/)


The BNS registry consists of a single smart contract that maintains a list of all domains and subdomains, and stores three critical pieces of information about each:

- The owner of the domain

- The resolver for the domain

- The caching time-to-live for all records under the domain

The owner of a domain may be either an external account (a user) or a smart contract. A registrar is simply a smart contract that owns a domain and issues subdomains of that domain to users that follow some set of rules defined in the contract.

Owners of domains in the ENS registry may:

- Set the resolver and TTL for the domain

- Transfer ownership of the domain to another address

- Change the ownership of subdomains

The BNS registry is deliberately straightforward and exists only to map from a name to the resolver responsible for it.

Resolvers are responsible for the actual process of translating names into addresses. Any contract that implements the relevant standards may act as a resolver in ENS. 

General-purpose resolver implementations are offered for users whose requirements are straightforward, such as serving an infrequently changed address for a name.

Each record type - cryptocurrency address, IPFS content hash, and so forth - defines a method or methods that a resolver must implement in order to provide records of that kind. New record types may be defined at any time via the BIP standardization process, 

with no need to make changes to the BNS registry or to existing resolvers in order to support them.

Resolving a name in BNS is a two-step process: First, ask the registry what resolver is responsible for the name, and second, ask that resolver for the answer to your query.