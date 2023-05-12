---
sidebar_position: 3
---

# Butane (Coming Soon) gRPC & REST

## Butane gRPC

Butane exposes gRPC endpoints for all the integrated Butane SDK modules. This makes it easier for
wallets and block explorers to interact with the Proof-of-Stake logic and native Butane transactions and queries.

## Butane HTTP REST (gRPC-Gateway)

[gRPC-Gateway](https://grpc-ecosystem.github.io/grpc-gateway/) reads a gRPC service definition and
generates a reverse-proxy server which translates RESTful JSON API into gRPC. With gRPC-Gateway,
users can use REST to interact with the Butane gRPC service. See the list
of supported gRPC-Gateway API endpoints using Swagger [here](../api#clients).
