---
id: Blockchain
created_date: 2024-10-23
updated_date: 2024-10-23
type: note
tags:
---

# Blockchain

## The Bitcoin Blockchain

Utilizes miners with distributed ledger system for verification (DLS). A miner says yes when the transaction is valid. The issue with this approach is that there could be malicious actors that send in incorrect verification.

Commercial users generate transactions. Once those transactions are signed with a private key and bundled into a "block" by some peers of the network. Then miners compete to find a hash value for the newly created "block."

A Bitcoin is a random number created by miners after completing Nakamoto consensus. Ledgers map coins to an address, which contains the owners public key. Once your private key is lost all the coins are lost.

Signing occurs with SHA-2 (256 bit) hashes using Elliptic Curve Digital Signature Algorithm (ECDSA).