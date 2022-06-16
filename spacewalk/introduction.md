# Introduction

**Spacewalk** is a pallet meant to act as a bridge between parachains in the Polkadot ecosystem and other chains. In particular, the first iteration of Spacewalk will allow users to bridge assets from the [Stellar Network](https://www.stellar.org/) to Substrate-based standalone chains and parachains.

You can read more about the bridge concept and how it works in our [blog post](https://pendulum-chain.medium.com/introducing-spacewalk-the-trust-minimized-bridge-between-stellar-and-pendulum-68ddbe7349a0), here we will focus on how to build & test it.

The project is in a Work in Progress state, so even though the pallet could be potentially plugged into any Substrate-based chain, for now we highly recommend that you follow this guide in order to properly test it.

{% hint style="info" %}
The following guide uses the provided testchain for convenience. The idea is to illustrate how to connect Spacewalk to a standalone chain. Connecting to the Pendulum chain show some differences that we address in [connecting-to-pendulum](connecting-to-pendulum/ "mention").
{% endhint %}
