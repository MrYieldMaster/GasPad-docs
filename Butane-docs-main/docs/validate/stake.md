---
sidebar_position: 7
---

# 🪄 Stake & Withdraw

## Stake, Delegate and Withdraw

The basic requirement to become a BBC chain validator is to have a stake amount of at least 10,000 BBC tokens. The stake amount is the sum of staked and delegated BBC tokens of the address. 

This guide walks trough the process of using MEW (MyEtherWallet.com) in the process of using Besc network. 

## Roadmap 

- Those functionalities will be built into our Studio and will not require any technical knowledge in the future.

 ## Stake
There are two options to stake (both should be called from the address which would be the validator)

- 1.1. Send $BBC tokens to the consensus contract - 0x... on the Butane network.

- 2.2. Call the `stake` function on the consensus contract - 0x.... on the Butane network.

## Delegate

$BBC token holders who don't want to run a node by themselves but still wish to participate in governing the network can delegate any amount to one of the validators. 

Delegating is done by calling the `delegate` function on the consensus contract with the validator address as data (see screenshot from MEW).

