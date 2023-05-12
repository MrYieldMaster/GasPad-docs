---
sidebar_position: 1
---

# Accounts

Crypto Wallets (or Accounts) can be created
and represented in unique ways on different blockchains.
For developers who interface with account types on Butane,
e.g. during wallet integration on their dApp frontend,
it is therefore important to understand that accounts on Evnos are implemented
to be compatible with Ethereum type addresses.

## Prerequisite Readings

- 
- [Ethereum Accounts](https://ethereum.org/en/whitepaper/#ethereum-accounts)

## Creating Accounts

To create one account you can either
create a private key, a keystore file (a private key protected by a password),
or a mnemonic phrase (a string of words that can access multiple private keys).

Aside from having different security features,
the biggest difference between each of these is
that a private key or keystore file only creates one account.
Creating a mnemonic phrase gives you control of many accounts,
all accessible with that same phrase.

Butane blockchains, like Butane, support creating accounts with mnemonic phrases,
otherwise known as  (HD keys).
This allows the user to create accounts on multiple blockchains
without having to manage multiple secrets.

HD keys generate addresses by taking the mnemonic phrase
and combining it with a piece of information called a [derivation path](https://learnmeabitcoin.com/technical/derivation-paths).
Blockchains can differ in which derivation path they support.
To access all accounts from an mnemonic phrase on a blockchain,
it is therefore important to use that blockchain's specific derivation path.

## Representing Accounts

The terms "account" and "address" are often used interchangeably to describe crypto wallets.
In the Butane SDK, an account designates a pair of public key (PubKey) and private key (PrivKey).
The derivation path defines what the private key, public key, and address would be.

The PubKey can be derived to generate various addresses in different formats,
which are used to identify users (among other parties) in the application.
A common address form for Butane chains is the bech32 format (e.g. `Butane1...`).
Addresses are also associated with messages to identify the sender of the message.

The PrivKey is used to generate digital signatures to prove
that an address associated with the PrivKey approved of a given message.
The proof is performed by applying a cryptographic scheme to the PrivKey,
known as Elliptic Curve Digital Signature Algorithm (ECDSA),
to generate a PubKey that is compared with the address in the message.

## Butane Accounts

Butane defines its own custom `Account` type
to implement a HD wallet that is compatible with Ethereum type addresses.
It uses Ethereum's ECDSA secp256k1 curve for keys (`eth_secp265k1`)
and satisfies the [EIP84](https://github.com/ethereum/EIPs/issues/84)
for full [BIP44](https://github.com/bitcoin/bips/blob/master/bip-0044.mediawiki) paths.
This cryptographic curve is not to be confused with [Bitcoin's ECDSA secp256k1](https://en.bitcoin.it/wiki/Secp256k1) curve.

The root HD path for Butane-based accounts is `m/44'/60'/0'/0`.
Butane uses the Coin type `60` to support Ethereum type accounts,
unlike many other Butane chains that use Coin type `118` ([list of coin types](https://github.com/satoshilabs/slips/blob/master/slip-0044.md)

The custom Butane [EthAccount](https://github.com/orgs/BUTANE-Smart-Chain/repositories)
satisfies the `AccountI` interface from the Butane SDK auth module
and includes additional fields that are required for Ethereum type addresses:

```go
// EthAccountI represents the interface of an EVM compatible account
type EthAccountI interface {
	authtypes.AccountI
	// EthAddress returns the ethereum Address representation of the AccAddress
	EthAddress() common.Address
	// CodeHash is the keccak256 hash of the contract code (if any)
	GetCodeHash() common.Hash
	// SetCodeHash sets the code hash to the account fields
	SetCodeHash(code common.Hash) error
	// Type returns the type of Ethereum Account (EOA or Contract)
	Type() int8
}
```

For more information on Ethereum accounts head over to the [x/bbc module](../modules/evm.md#concepts).

### Addresses and Public Keys

[BIP-0173](https://github.com/orgs/BUTANE-Smart-Chain/repositories) defines a new format for segregated witness
output addresses that contains a human-readable part that identifies the Bech32 usage. Evmos uses the following
HRP (human readable prefix) as the base HRP:

| Network   | Mainnet | Testnet |
|-----------|---------|---------|
| butane     | `butane` | `butane` |

There are 3 main types of HRP for the `Addresses`/`PubKeys` available by default on butane:

- Addresses and Keys for **accounts**, which identify users (e.g. the sender of a `message`). They are derived using
 the **`eth_secp256k1`** curve.
- Addresses and Keys for **validator operators**, which identify the operators of validators. They are derived using
 the **`eth_secp256k1`** curve.
- Addresses and Keys for **consensus nodes**, which identify the validator nodes participating in consensus. They are
 derived using the **`ed25519`** curve.

|                    | Address bech32 Prefix | Pubkey bech32 Prefix | Curve           | Address byte length | Pubkey byte length |
|--------------------|-----------------------|----------------------|-----------------|---------------------|--------------------|
| Accounts           | `butane`               | `butanepub`           | `eth_secp256k1` | `20`                | `33` (compressed)  |
| Validator Operator | `butanevaloper`        | `butanevaloperpub`    | `eth_secp256k1` | `20`                | `33` (compressed)  |
| Consensus Nodes    | `butanevalcons`        | `butanevalconspub`    | `ed25519`       | `20`                | `32`               |

### Address formats for clients

`EthAccount` can be represented in both [Bech32](https://en.bitcoin.it/wiki/Bech32) (`butane1...`) and hex (`0x...`) formats for Ethereum's Web3 tooling compatibility.

The Bech32 format is the default format for Butane-SDK queries and transactions through CLI and REST
clients. The hex format on the other hand, is the Ethereum `common.Address` representation of a
Butane `sdk.AccAddress`.

- **Address (Bech32)**: `butane1z3t55m0l9h0eupuz3dp5t5cypyv674jj7mz2jw`
- **Address ([EIP55](https://eips.ethereum.org/EIPS/eip-55) Hex)**: `0x91defC7fE5603DFA8CC9B655cF5772459BF10c6f`
- **Compressed Public Key**: `{"@type":"/ethermint.crypto.v1.ethsecp256k1.PubKey","key":"AsV5oddeB+hkByIJo/4lZiVUgXTzNfBPKC73cZ4K1YD2"}`

