---
sidebar_position: 2
---

# Oracles

Oracles are a crucial component of the decentralized web, enabling smart contracts to access off-chain data and interact
 with the real world.
These oracles serve as a bridge between the decentralized, trustless environment of blockchain and the centralized,
traditional internet.

An oracle is a piece of software that retrieves data from external sources and feeds it into smart contracts on the blockchain.
This enables smart contracts to respond to real-world events, trigger automated actions, and execute their intended functions.

Evmos partners with several oracles providers to help provide value feed services and more.

Our oracles include:

- [Adrastia](https://docs.adrastia.io/)
- [DIA](https://docs.diadata.org/introduction/readme)
- [SEDA Network](https://docs.seda.xyz/seda-network/introduction/the-oracle-problem) - Flux has renamed to SEDA Network
- [Redstone](https://docs.redstone.finance/docs/introduction)
- [Pyth](https://docs.pyth.network/)

``` sql
   +------------+         +------------+         +-------------+
   | External   |         |   Oracle   |         |  Smart      |
   | Data Source|         | Service    |         | Contract    |
   +------------+         +------------+         +-------------+
        |                       |                       |
        |  API Call             |                       |
        |---------------------> |                       |
        |                       |    Retrieve External  |
        |                       |    Data via API Call  |
        |                       |---------------------->|
        |                       |                       |
        |                       |    Use External Data  |
        |                       |    in Smart Contract  |
        |                       |<----------------------|
        |                       |                       |
        |                       |    Return Result to   |
        |                       |    Smart Contract     |
        |                       |<----------------------|
        |                       |                       |

```

In this diagram:

External Data Source refers to a source of data outside the blockchain network, such as a stock market, weather service,
 or other external API.

Oracle Service is a third-party service that acts as a bridge between the external data source and the smart contract.
 It retrieves the data from the external source and provides it to the smart contract.

Smart Contract is a self-executing contract that is deployed on the blockchain network. It uses the data provided by the
 oracle to perform certain actions, such as releasing funds or triggering events.

API Call refers to the request made by the smart contract to the oracle service, asking for the required external data.

Retrieve External Data refers to the process of retrieving the requested data from the external data source via the API call.

Use External Data refers to the process of using the retrieved data in the smart contract to perform actions, such as
condition checking and state changes.

Return Result refers to the process of returning the result of the action performed in the smart contract back to the oracle.

## Features of Oracles

- Data Feeds
    - Token
    - NFT
    - TradFi
- Randomness

## Partner Details

### Adrastia (Coming Soon)


### Redstone

RedStone offers a radically different design of Oracles catering for the needs of modern Defi protocols.

- Data providers can avoid the requirement of continuous on-chain data delivery
- Allow end users to self-deliver signed Oracle data on-chain
- Use the decentralized Streamr network to deliver signed oracle data to the end users
- Use token incentives to motivate data providers to maintain data integrity and uninterrupted service
- Leverage the Arweave blockchain as a cheap and permanent storage for archiving Oracle data and maintaining data
providers' accountability

```
# Using yarn
yarn add @redstone-finance/evm-connector

# Using NPM
npm install @redstone-finance/evm-connector
```

Examples of Redstone EVM Connector can be found [here](https://github.com/redstone-finance/redstone-evm-connector-examples/blob/main/contracts/example-custom-urls.sol).

### Pyth

Pyth leverages over [70 first-party publishers](https://pyth.network/publishers) to publish financial market data to numerous blockchains.
They provide data feeds to various assets classes, such as [US equities, commodities, and cryptocurrencies](https://pyth.network/price-feeds/). The service has undergone several audits and more information can be found [here](https://github.com/pyth-network/audit-reports).

- [Developer Docs](https://docs.pyth.network/)
- [Pyth Client for Linux](https://github.com/pyth-network/pyth-client)
- [Pyth TS client NPM](https://www.npmjs.com/package/@pythnetwork/client)

### SEDA network

[SEDA Rust library](https://github.com/sedaprotocol/seda-rust)

Going beyond today’s definition of an oracle, SEDA is a multi-chain-native data transmission protocol built on an
entirely decentralized foundation. The SEDA network is a Proof-of-Stake on-chain data provision solution that
allows anyone to provide and access high-quality data on all blockchain networks. It is a living market and transport
layer that enables access and flow for any type of data through a transparent and secure medium, free of centralized intermediaries.
