# Introduction

**Spacewalk** is a pallet meant to act as a bridge between parachains in the Polkadot ecosystem and other chains. In particular, the first iteration of Spacewalk will allow users to bridge assets from the [Stellar Network](https://www.stellar.org/) to a standalone chain based on Substrate. In a next iteration, the pallet will be included in the Pendulum chain as a core part of it.

You can read more about the bridge concept and how it works in our [blog post](https://pendulum-chain.medium.com/introducing-spacewalk-the-trust-minimized-bridge-between-stellar-and-pendulum-68ddbe7349a0), here we will focus on how to build & test it.&#x20;

The project is in a Work in Progress state, so even though the pallet could be potentially plugged into any Substrate-based chain, for now we highly recommend that you follow this guide in order to properly test it.

{% hint style="success" %}
This guide will cover how to build the parts needed for the bridge to work, and a simple testing scenario in which we will bridge assets from the Stellar network to a _testchain_, and then redeem the funds, bridging them back to Stellar.
{% endhint %}
