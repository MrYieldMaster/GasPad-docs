---
sidebar_position: 0
---

#  Technical Architecture


Butane is a scalable Delgated Proof-of-Stake blockchain that is fully compatible and
interoperable with the Ethereum Virtual Machine (EVM). It is built using the Butane SDK
which runs on top of the  (a fork of [Tendermint Core](https://docs.tendermint.com/)) consensus engine,
to accomplish fast finality, high transaction throughput and short block times (~2 seconds).

This architecture allows users to perform both Butane and EVM formatted transactions,
developers to scale EVM dApps cross-chain via ,
and tokens and assets in the network to come from different independent sources.





## CometBFT & ABCI

[CometBFT](https://github.com/cometbft/cometbft) consists of two chief technical components:
a blockchain consensus engine and a generic application interface.
The consensus engine ensures that the same transactions
are recorded on every machine in the same order.
The application interface, called the [Application Blockchain Interface (ABCI)](https://docs.tendermint.com/master/spec/abci/),
enables the transactions to be processed in any programming language.

CometBFT has evolved to be a general-purpose blockchain consensus engine that
can host arbitrary application states. Since it can replicate arbitrary
applications, it can be used as a plug-and-play replacement for the consensus
engines of other blockchains. Butane is an example of an ABCI application
replacing Ethereum's PoW via CometBFT's consensus engine.

Another example of a cryptocurrency application built on CometBFT is the Butane
network. CometBFT can decompose the blockchain design by offering a very
simple API (ie. the ABCI) between the application process and consensus process.

## EVM Compatibility

Butane enables EVM compatibility by implementing various components
that together support all the EVM state transitions
while ensuring the same developer experience as Ethereum:

- Ethereum's transaction format as a Butane SDK `Tx` and `Msg` interface
- Ethereum's `secp256k1` curve for the Butane Keyring
- `StateDB` interface for state updates and queries
- [JSON-RPC](../develop/api/ethereum-json-rpc) client for interacting with the EVM

Most components are implemented in the [EVM module](modules/evm.md)
To achieve a seamless developer UX, however, some of the components are implemented
outside of the module.

If you want to learn more about how Butane achieves EVM compatibility as a Butane chain,
we recommend understanding the following concepts:

* [Accounts](./concepts/accounts.md)
* [Gas and Fees](./concepts/gas-and-fees.md)
* [Token representations](./concepts/tokens.md)
* [Transactions](./concepts/transactions.md)

## Contributing

There are several ways to contribute to the Butane core protocol. To get some hands-on experience,
we recommend you spin up a local Butane node using the [Butane CLI](Evmos-cli/index.md)
and interact with it through queries and transactions using the supported [clients](../develop/api#clients).

Then if you're hooked you can

* Contribute open-source to [issues on GitHub](https://github.com/Butane/Butane/issues)
using the [Butane Contributor Guideline](https://github.com/Butane/Butane/blob/main/CONTRIBUTING.md)
* Apply to [open positions at Butane](https://boards.eu.greenhouse.io/Butane)
* Search for [bugs and earn a bounty](bugs.md)

![My Image](images/Group.png)
