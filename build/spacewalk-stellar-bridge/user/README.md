---
description: >-
  The Spacewalk bridge system acts as a connection between two networks: the
  Stellar network and any Substrate-based chain.
---

# User

The user can select a vault and initiate the token transfer process with a request\_redeem signalling the intent to bridge tokens from Parachain for the Stellar chain. Vault processes the request within a specified timeframe.

To bridge from Stellar to the Parachain, users choose a vault, send a request\_issue, transfer assets to the vault using the issue\_id, and the vault executes the issuance. When bridging from the Parachain to Stellar, users select a vault, send a request\_redeem, and the vault has a defined time frame to transfer assets to the user on the Stellar chain.

**Main Flows:**

**Stellar to Parachain:**

Initiate the transfer of Spacewalk assets from the Stellar network to any Parachain

**Parachain to Stellar:**

Transferring assets from a Substrate-based Parachain back to the Stellar network
