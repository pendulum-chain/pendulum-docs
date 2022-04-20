# Highlights

## Fiat tokens availability

One of the core pillars of Pendulum is its capacity to collect and connect fiat-pegged tokens from the most prominent blockchain ecosystems into a single, optimized blockchain system. By giving project developers and token holders access to a broad basket of fiat tokens, Pendulum unlocks an evolution in money markets and borderless financial transactions.&#x20;

Connecting across different ecosystems requires different solutions depending on the nature of the target network: in some cases it will be network-specific bridges, in other integrations into multichain bridges or the DotSama relay chain through the cross-chain messaging protocol. In order to ensure that the bridged tokens are distributed as wide as possible within the DotSama ecosystem, a Statemine/Statemint integration is planned. One key design principle is to ensure that the bridge technologies are as trustless and robust as possible. In the below section, we will look at some of the planned bridge technologies and options.

### Spacewalk: Stellar bridge

The [Stellar network](https://www.stellar.org/?locale=en) is an open blockchain with a focus on efficiency in speed and transaction costs, as well as integrations into the traditional financial system. It has a rich ecosystem with a focus on compliant fiat-pegged tokens and local (as well as instant, in a growing number of countries) fiat on- and offramps. Historically, Stellar has been optimized for speed and low transaction costs and not to execute sophisticated smart contracts at scale, which has largely isolated the network from the DeFi industry. Connecting Stellar with the DotSama ecosystem means that it will be possible for Stellar tokens to be exposed to more sophisticated smart contracts, while users in the DotSama ecosystem expand the basket of available fiat tokens.&#x20;

Spacewalk is the first bridge between the Stellar network and the DotSama ecosystems. Based on [XCLAIM](http://xclaim.io) and [interBTC](http://github.com/interlay/interbtc), it is implemented as a Substrate pallet and allows any Substrate-based blockchain to implement a direct Stellar bridge.

The architecture of the bridge consists of the following components:&#x20;

1. **Vaults**: this is a set of escrow accounts used to lock assets in Stellar. Their behavior is defined in XCLAIM and interBTC. In Spacewalk they have an additional property: each vault has an allowlist of assets that it can lock and support for bridging operations between Stellar and the Substrate chain. This allowlist is implemented through [trustlines](https://developers.stellar.org/docs/issuing-assets/anatomy-of-an-asset/#trustlines) of the Stellar account. There can be at most 1000 supported assets per vault due to limitations in Stellar. Stellar users initiate a deposit by sending tokens to an appropriate vault, which they request from the bridge pallet prior to the deposit. Likewise vaults will unlock and send tokens back to Stellar accounts during a withdrawal. Every vault needs to provide collateral with DOT or KSM (or related) tokens with the bridge pallet. These tokens are slashed in case the vault misbehaves.
2. **Bridge Pallet**: this is the main component of the Spacewalk bridge that implements all logic on the side of the Substrate-based chain. Its behavior is based on interBTC. It is particularly responsible for minting tokens during deposits and burning tokens during withdrawals. It is able to support any Stellar asset by employing the [Tokens](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/tokens) and [Currencies](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/currencies) pallets of the Substrate Open Runtime Module Library. The storage of the bridge pallet maintains the complete state that is required for the bridge to work correctly. This state contains (among others): the account ids of the vaults, the asset allow lists of each vault and book keeping information about the state of the Stellar network.&#x20;
3. **Stellar Oracle**: is a decentralized system that provides information about the state of the Stellar network to the bridge pallet. In interBTC this is implemented through a Bitcoin chain relay. However, for reasons explained above we cannot implement a chain relay for Stellar in the same way. The Stellar oracle is trustless and reliable and its functionality is based on specific unique aspects of Stellar:&#x20;
   1. The Stellar network has multiple tier levels, where the nodes in Tier 1 enjoy the highest level of trust of its peers. There are currently 23 Tier 1 nodes; this set and its structure is rather static and only changes rarely. It only ever changes through a voting process. We will incorporate complete information about the Tier 1 network in the bridge pallet.&#x20;
   2. Every Stellar node has a static signing key pair and signs messages that it gossips to the network. Particularly, every node announces through a signed message that a block has been finalized. The decentralized oracle will forward these signed messages from Tier 1 nodes to the bridge pallet. This way the bridge pallet can reliably infer what Stellar blocks are finalized.

### Cosmos bridge

Similar to Polkadot, Cosmos is a decentralized ecosystem of independent parallel blockchains that can scale and interoperate with each other via a common messaging standard. This network of networks has seen enormous growth and some of the most popular fiat-pegged tokens in the cryptocurrency sphere.

Pendulum’s Cosmos bridge will be based on the [Substrate-IBC pallet](https://github.com/octopus-network/substrate-ibc) developed by [Astar](https://astar.network).

### Ethereum bridge

Ethereum is still the “grand old dame” of smart contract blockchains and has served as the basis for many popular layer 2 networks. The Ethereum-Pendulum bridge will be based on modules developed by third parties. At the time of writing, there are two candidates: ChainBridge and SnowBridge.

Today, ChainBridge seems the most likely candidate. It is a bridge between the Ethereum Virtual Machine (“EVM”) and Pendulum, which allows bridging tokens on Pendulum to Ethereum as ERC-20 tokens. At the high level, the ChainBridge process is represented in the diagram below:

ChainBridge operates under a trusted federation model, where a trusted set of off-chain relayers coordinate the transfer between one chain to the other. According to ChainSafe, the developers behind the project, there is a plan to make the bridge more trustless.

SnowBridge is still under development, but when a stable version is released, it promises to offer both ERC-20  and ERC-721 (non-fungible tokens) transfers as well as general-purpose smart contract invocations.

### Real chain integration (XCMP)

The relay chain sits at the heart of the Polkadot and Kusama networks of networks; it provides both security and interoperability between the parachains. The cross-consensus message format (XCM) describes the methods for message transfer between different consensus systems. Cross-chain message passing (XCMP) is a protocol that builds on the XCM architecture. The XCMP protocol allows parachains to exchange messages with other parachains on the same relay chain and guarantees the delivery of these messages. The message delivery is not only guaranteed but also trustless, meaning that Polkadot's shared security ensures the correctness and ordering of the message delivery.

To communicate, parachains first have to establish a messaging communication channel with each other. These channels are one-way, but there can be up to 1 channel for every (sender, recipient) parachain pair, allowing bidirectional communication. The channels work with a queue of ordered messages queued by the sender and eventually acknowledged by the recipient parachain. Both parachains are expected to monitor the state of the relay chain to know what is currently in the message queue. However, "XCM is not designed in that every system supporting the format is expected to be able to interpret any possible XCM message. Practically speaking, one can imagine that some messages will not have reasonable interpretations under some systems or will be intentionally unsupported." \[Source: https://wiki.polkadot.network/docs/learn-crosschain]

While it can be used in many ways, the most common use-case for inter-chain messaging is probably handling and moving assets between different parachains. For example, XCM allows the teleportation of assets between different parachains. Pallets like the ['xtokens'](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/xtokens) module make it easy for parachains to leverage the capabilities of XCM to integrate cross-chain token transfer functionalities to their parachain. This is optional however, since every chain has to proactively set up communication channels with other chains and listen to respective messages.

At the time of writing, XCMP is still in development. For the time being, the Horizontal Relay-routed Message Passing (HRMP) protocol is in place that has the same interface and functionality as XCMP but is more demanding on resources.

## Fait token quality

With any open-ended and permissionless system comes a relatively high level of noise compared to closed and censured systems. With the explosion in fiat stabletokens, it is natural that some have been more robust and trustworthy than others. As Pendulum plans to attract high-quality fiat tokens from around different ecosystems, there should be some mechanisms that encourage the best of tokens to be promoted and widely used on the network. This mechanism is part of the decentralized governance structure of Pendulum.

Overall, the Pendulum on-chain governance process is expected to be established similarly to the core[ Polkadot governance mechanism](https://polkadot.network/blog/polkadot-governance/), with one additional feature: a token committee. Much like the The Technical Committee on the Polkadot, the token committee has been granted the right to award a limited set of assets on the network favorable terms, such as lower transaction fees, if they fulfill certain standards. This structure incentivizes quality tokens and their use.

## Traditional finance networks integrations

Building integrations into the traditional financial networks broadens the scope of Pendulum, as both consumers and financial institutions are able to participate in the network activities. With an emphasis on both the fiat deposit and withdrawal processes and an optional data layer for the transmission and management of compliance processes, Pendulum allows dApps to build seamless consumer user experiences.

### Direct fiat on/off ramp

The often complex user journey when moving funds from traditional financial institutions onto blockchain has been one of the major obstacles in the way to broad adoption of cryptocurrencies and blockchain technology as a whole. Pendulum reduces this barrier with a twofold approach: direct on/offramp partners and ramping standards. On/offramps (“ramps” or “anchors”) services are entities converting fiat currency to tokens on a blockchain and vice versa. By encouraging such fiat ramps to integrate directly into the Pendulum network, customers can on/offramp between Pendulum and their local banking networks in their native fiat currency.

To further encourage ramp integrations, Pendulum will develop open source ramp standards — the technical and business rules by which a ramping service should act — which will be usable for any ramp in the entire DotSama ecosystem. By driving innovative ramping solutions to the network, Pendulum will foster more liquidity and closer cross-parachain interoperability.

### Opt-in complaince data layer

In order to make the TradFi integrations as seamless as possible, Pendulum includes a voluntary and trustless data layer for the transmission of compliance data. The layer governs the secure, end-to-end encrypted passing of information between two entities on the network, for example, in the context of an offramp transaction. The standard is currently being defined alongside experienced compliance service providers with the goal of minimizing the number of compliance checks that a given customer must undertake in the process of interacting with multiple regulated services. For example, a customer may onramp with credit card in one country, but eventually offramp with a neobank in another — the customer can in this case volunteer to let the two services securely share the compliance data, thereby avoiding multiple compliance processes.

## Next generation smart contracts

Pendulum is built on [Substrate](http://substrate.dev), a blockchain framework developed by [Parity Technologies](http://parity.io). The framework was used to build both [Polkadot](http://polkadot.network) and Kusama. The advantages of Substrate are many: in addition to having native compatibility with the Polkadot chain, Substrate has cross-coding language support, forkless upgrades with built-in upgrade coordination, deterministic finality (for fast consensus reaching), and a suite of pre-built but customizable components (“pallets”).

As a framework, Substrate comes with a wide range of features for creating and deploying a blockchain system, which can be customized according to preference. The following section presents a highlight of some of the technical decisions of the Substrate implementation and the reasoning behind them.

In order to bring the most capabilities and affordances to developers, Pendulum will introduce and implement a suite of next-generation smart contract technologies. The approach is twofold: implement, invest and develop [WebAssembly](http://webassembly.org) (“Wasm”), which is the future of smart contract execution layers, while also supporting the incumbent Ethereum Virtual Machine (“EVM”), which, despite some of its limitations, is still favored by a large number of developers.

### WebAssembly

Wasm, a Web-technology developed and maintained by a W3C workgroup that includes, among others, Google and Mozilla is heralded as the next base layer for decentralized applications. Using Wasm for smart contracts has lots of advantages like performance that is near native machine code, a small size, and efficient just-in-time execution. Smart contracts can be written in any of the many languages that can compile to Wasm, including C/C++, Rust, Go, and also Solidity, the most widely used programming language for smart contracts. Pendulum developers will be able to write smart contracts in the language of their choice and use existing tools and methods, which ultimately flattens the learning curve for the community and decreases implementation costs for dApp and project builders.

While Wasm has already seen broad adoption on the open Web, the integration into blockchain systems is still in its early stages. For the long awaited Ethereum 2.0, Wasm has been worked on as a candidate for an [EVM replacement](http://ewasm.readthedocs.io/en/mkdocs), but not yet fully finalized. Within the DotSama ecosystem, Pendulum is participating in the community effort to improve the performance and security of Wasm.

### EVM&#x20;

The EVM is a milestone in the history of blockchain technology, the very first smart contract execution engine. However, it is quite inefficient because every instruction operates on 256 bit values, which is unnecessary complex for most applications. This makes executing smart contracts for EVM quite inefficient compared to WebAssembly. Nevertheless it is still the most popular virtual machine standard for smart contracts.

Substrate comes with a library of modules called [Frontier](https://github.com/paritytech/frontier) that allow to create an Ethereum compatibility layer. Frontier comprises an EVM execution engine which can run EVM smart contracts, in particular, smart contracts that have been written in Solidity and compiled to EVM byte code. For every Substrate account there will be an associated Ethereum address so that users can operate with Ethereum-like addresses instead of with the native address format of Substrate. Furthermore, it provides an Ethereum compatible RPC interface so that users can utilize their familiar wallets from the Ethereum ecosystem, e.g., via Metamask

Pendulum will integrate Frontier to allow execution of smart contracts originally written for Ethereum and compatible blockchains. One the one hand this allows Pendulum and its community of developers to tap into the massive library of readily available Ethereum smart contracts and on the other hand smart contract creators can directly deploy their projects to Pendulum and utilize them for the basket of stablecoins accessible on Pendulum. This hybrid approach of the contracts pallet and Frontier combines the best of both worlds and allows smart contract creators to use their favorite programming language and to target their favorite machine.

## Scalability

Coming soon

## Privacy & Security

Coming soon

### MEV protection

Coming soon

