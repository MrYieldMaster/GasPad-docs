---
sidebar_position: 9
---
# Multisig

Learn how to generate, sign and broadcast a transaction using the keyring multisig.

A **multisig account** is an butane account with a special key that can require more than one signature to sign transactions.
 This can be useful for increasing the security of the account or for requiring the consent of multiple parties to make
  transactions. Multisig accounts can be created by specifying:

- threshold number of signatures required
- the public keys involved in signing

To sign with a multisig account, the transaction must be signed individually by the different keys specified for the account.
 Then, the signatures will be combined into a multi-signature which can be used to sign the transaction. If fewer than the
  threshold number of signatures needed are present, the resultant multi-signature is considered invalid.

## Generate a Multisig key

```bash
butaned keys add --multisig=name1,name2,name3[...] --multisig-threshold=K new_key_name
```

`K` is the minimum number of private keys that must have signed the transactions that carry the public key's address as signer.

The `--multisig` flag must contain the name of public keys that will be combined into a public key that will be
generated and stored as `new_key_name` in the local database. All names supplied through `--multisig` must already exist
 in the local database.

Unless the flag `--nosort` is set, the order in which the keys are supplied on the command line does not matter, i.e. the
 following commands generate two identical keys:

```bash
butaned keys add --multisig=p1,p2,p3 --multisig-threshold=2 multisig_address
butaned keys add --multisig=p2,p3,p1 --multisig-threshold=2 multisig_address
```

Multisig addresses can also be generated on-the-fly and printed through the which command:

```bash
butaned keys show --multisig-threshold=K name1 name2 name3 [...]
```

## Signing a transaction

### Step 1: Create the multisig key

Let's assume that you have `test1` and `test2` want to make a multisig account with `test3`.

First import the public keys of `test3` into your keyring.

```sh
butaned keys add \
    test3 \
    --pubkey=butanepub1addwnpepqgcxazmq6wgt2j4rdfumsfwla0zfk8e5sws3p3zg5dkm9007hmfysxas0u2
```

Generate the multisig key with 2/3 threshold.

```sh
butaned keys add \
    multi \
    --multisig=test1,test2,test3 \
    --multisig-threshold=2
```


### Step 2: Create the multisig transaction



The file `unsignedTx.json` contains the unsigned transaction encoded in JSON.

```json
{
  "body": {
    "messages": [
      {
        "@type": "/cosmos.bank.v1beta1.MsgSend",
        "from_address": "0x...",
        "to_address": "butane157g6rn6t6k5rl0dl57zha2wx72t633axqyvvwq",
        "amount": [
          {
            "denom": "abutane",
            "amount": "5000000000000000000"
          }
        ]
      }
    ],
    "memo": "",
    "timeout_height": "0",
    "extension_options": [],
    "non_critical_extension_options": []
  },
  "auth_info": {
    "signer_infos": [],
    "fee": {
      "amount": [
        {
          "denom": "abutane",
          "amount": "1000000"
        }
      ],
      "gas_limit": "200000",
      "payer": "",
      "granter": ""
    }
  },
  "signatures": []
}
```

### Step 3: Sign individually

Sign with `test1` and `test2` and create individual signatures.

```sh
butaned tx sign \
    unsignedTx.json \
    --multisig=butane1e0fx0q9meawrcq7fmma9x60gk35lpr4xk3884m \
    --from=test1 \
    --output-document=test1sig.json \
    --chain-id=butane_9000-4
```

```sh
butaned tx sign \
    unsignedTx.json \
    --multisig=butane1e0fx0q9meawrcq7fmma9x60gk35lpr4xk3884m \
    --from=test2 \
    --output-document=test2sig.json \
    --chain-id=butane_9000-4
```

### Step 4: Create multisignature

Combine signatures to sign transaction.

```sh
butaned tx multisign \
    unsignedTx.json \
    multi \
    test1sig.json test2sig.json \
    --output-document=signedTx.json \
    --chain-id=butane_9000-4
```

The TX is now signed:



### Step 5: Broadcast transaction

```sh
butaned tx broadcast signedTx.json \
    --chain-id=butane_9000-4 \
    --broadcast-mode=block
```
