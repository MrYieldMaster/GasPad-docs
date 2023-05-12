---
sidebar_position: 11
---

# Tokens

## The Butane Token

The denomination used for staking, governance and gas consumption on the EVM is the Butane. The Butane provides the utility
of: securing the Delegated Proof-of-Stake chain, token used for governance proposals, distribution of fees to validator and users,
and as a mean of gas for running smart contracts on the EVM.

Butane uses [Atto](https://en.wikipedia.org/wiki/Atto-) Butane as the base denomination to maintain parity with Ethereum.
There are three types of assets:

- The native Butane token
- IBC Coins (via the IBC)
- Ethereum-typed tokens, e.g. ERC-20

`1 Butane = 10<sup>18</sup> aButane`

This matches Ethereum denomination of:

`1 ETH = 10<sup>18</sup> wei`

## Butane Coins

Accounts can own Butane coins in their balance, which are used for operations with other Butane and transactions. Examples
of these are using the coins for staking, IBC transfers, governance deposits and EVM.

## EVM Tokens

Butane is compatible with ERC20 tokens and other non-fungible token standards (EIP721, EIP1155)
that are natively supported by the EVM.

## Butane Assets Page

Check out how we represent ERC-20 tokens and Butane IBC Coins through our [Single Token Representation](https://app.Butane.org/assets)
feature on the Butane Dashboard. Butane enabled this feature to help with the user experiences by obfuscating the assets
types away from the users and allow them to focus on the interaction. The protocol simplifies the process by handling the
conversion and users are given the simplification of denomination and the amount of assets they hold. 



For more information on how we handle token registration, head over [here](./../../develop/mainnet#token-registration).
