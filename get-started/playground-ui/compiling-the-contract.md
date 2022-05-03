# Compiling the contract

The Pendulum AMM smart contract was developed with [ink!](https://github.com/paritytech/ink) and adapted from the Uniswap V2 contracts. If you want to deploy another smart contract and already have the `.contract` file of that contract you can skip these steps and go straight to the next section.

## Compilation of the smart contract

1. Follow the steps [here](https://paritytech.github.io/ink-docs/getting-started/setup/) to set up your Rust & ink! environment
2. Clone the [pendulum amm](https://github.com/pendulum-chain/pendulum-amm) repository
3. Enter the root directory of the repository and run `cargo +nightly contract build`.

This will compile the contract and create a `.contract` file that bundles the WASM binary and metadata. This `.contract` file can be used to deploy your contract to a chain. You can find it in `./target/ink/pendulum_amm.contract`.

{% hint style="info" %}
If you don't want to compile the smart contract yourself, you can also find the resulting `pendulum_amm.contract` file in the GitHub releases directory [here](https://github.com/pendulum-chain/pendulum-amm/releases).
{% endhint %}
