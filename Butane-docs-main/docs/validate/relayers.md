---
sidebar_position: 6
---

# 💨 Run an IBC Relayer

## What is an IBC Relayer?

An IBC relayer is a software component that facilitates communication between two distinct blockchain networks that
support the Inter-Blockchain Communication (IBC) protocol. The IBC protocol is a standard for the secure and reliable
 transfer of digital assets and data across different blockchain networks.

An IBC relayer is responsible for relaying IBC packets, which are used to send messages and data between two different
 blockchain networks. It receives packets from one chain, verifies their authenticity and validity, and then relays
  them to the receiving chain.

## Minimum Requirements

- 8 core (4 physical core), x86_64 architecture processor
- 32 GB RAM (or equivalent swap file set up)
- 1 TB+ nVME drives

If running many nodes on a single VM, [ensure your open files limit is increased](https://tecadmin.net/increase-open-files-limit-ubuntu/).

## Prerequisites

Before beginning, ensure you have an Evmos node running in the background of the same machine that you intend to relay on.
 Follow [this guide](./../protocol/evmos-cli/single-node) to set up an Evmos node if you have not already.

