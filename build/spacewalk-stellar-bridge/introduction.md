---
description: Stellar-Polkadot bridge
---

# Introduction

Spacewalk will enable Pendulum chain to utilize the multitude of fiat stable tokens on the Stellar blockchain and help build the fiat DeFi future. Spacewalk is the first bridge between the Stellar network and the Polkadot/Kusama ecosystems, which opens up a flow of stable tokens from the Stellar network. Based on XCLAIM and interBTC, it is implemented as a Substrate pallet and allows any Substrate-based blockchain to implement a direct Stellar bridge.

Spacewalk will be a trustless and decentralized bridge built to connect Pendulum and Stellar, but it can also be plugged into any Substrate-based blockchain on Polkadot. You can read more about the bridge concept and how it works in our [blog post](https://pendulum-chain.medium.com/introducing-spacewalk-the-trust-minimized-bridge-between-stellar-and-pendulum-68ddbe7349a0), here we will focus on how to build & test it.

The project is in a Work in Progress state, so even though the pallet could be potentially plugged into any Substrate-based chain, for now we highly recommend that you follow this guide in order to properly test it.

{% hint style="info" %}
The following guide uses the provided testchain for convenience. The idea is to illustrate how to connect Spacewalk to a standalone chain. Connecting to the Pendulum chain show some differences that we address in [connecting-to-pendulum](connecting-to-pendulum/ "mention").
{% endhint %}
