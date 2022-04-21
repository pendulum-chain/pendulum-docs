# Next generation smart contracts

Pendulum is built on [Substrate](http://substrate.dev), a blockchain framework developed by [Parity Technologies](http://parity.io). The framework was used to build both [Polkadot](http://polkadot.network) and Kusama. The advantages of Substrate are many: in addition to having native compatibility with the Polkadot chain, Substrate has cross-coding language support, forkless upgrades with built-in upgrade coordination, deterministic finality (for fast consensus reaching), and a suite of pre-built but customizable components (“pallets”).

As a framework, Substrate comes with a wide range of features for creating and deploying a blockchain system, which can be customized according to preference. The following section presents a highlight of some of the technical decisions of the Substrate implementation and the reasoning behind them.

In order to bring the most capabilities and affordances to developers, Pendulum will introduce and implement a suite of next-generation smart contract technologies. The approach is twofold: implement, invest and develop [WebAssembly](http://webassembly.org) (“Wasm”), which is the future of smart contract execution layers, while also supporting the incumbent Ethereum Virtual Machine (“EVM”), which, despite some of its limitations, is still favored by a large number of developers.



