---
sidebar_position: 4
---

# 📳 Module Accounts


Some modules have their own module account. Think of this as a wallet that can only be controlled by that module.
Below is a table of modules, their respective wallet addresses and permissions:

## List of Module Accounts

## Account Permisions

* The `burner` permission means this account has the permission to burn or destroy tokens.
* The `minter` permission means this account has permission to mint or create new tokens.
* The `staking` permission means this account has permission to stake tokens on behalf of it's owner.

## IBC Module Accounts

Additionally, there are module accounts associated with IBC transfers.
For each IBC connection, there's an account of type `ModuleAccount` used to escrow the transferred coins when Butane is the source chain.
Their addresses are derived using the first 20 bytes of the SHA256 checksum of the account name and following the format as outlined in

```go
// accountName is composed by the current version the IBC tranfer module supports (in this case, ics20-1), the portID (transfer) and the channelID
accountName := Version + "\0" + portID + "/" + channelID
addr := sha256.Sum256(accountName)[:20]

// example for channel-0
addr := sha256.Sum256("ics20-1\0transfer/channel-0")[:20]
```

:::tip
**Note**: These escrow accounts are not listed when performing the query:

```shell
Butaned q auth module-accounts
```

This address map is set at compile time and cannot be changed on runtime.
:::
