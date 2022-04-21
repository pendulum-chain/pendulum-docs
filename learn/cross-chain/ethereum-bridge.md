# Ethereum bridge

Ethereum is still the “grand old dame” of smart contract blockchains and has served as the basis for many popular layer 2 networks. The Ethereum-Pendulum bridge will be based on modules developed by third parties. At the time of writing, there are two candidates: ChainBridge and SnowBridge.

Today, ChainBridge seems the most likely candidate. It is a bridge between the Ethereum Virtual Machine (“EVM”) and Pendulum, which allows bridging tokens on Pendulum to Ethereum as ERC-20 tokens. At the high level, the ChainBridge process is represented in the diagram below:

ChainBridge operates under a trusted federation model, where a trusted set of off-chain relayers coordinate the transfer between one chain to the other. According to ChainSafe, the developers behind the project, there is a plan to make the bridge more trustless.

SnowBridge is still under development, but when a stable version is released, it promises to offer both ERC-20  and ERC-721 (non-fungible tokens) transfers as well as general-purpose smart contract invocations.
