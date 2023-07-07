# Building pallets and testchain

## Before Building

Make sure you have completed the basic Rust setup, see [here](https://github.com/pendulum-chain/spacewalk/blob/main/testchain/docs/rust-setup.md) for more information

## Building the Testnet

A pallet cannot run by itself in an isolated way. It needs to be part of a runtime to expose its functionality. In this chapter, you're going to build the first fundamental part of our testing scenario, which is a local testnet that already contains the Spacewalk pallet.

If you navigate to [https://github.com/pendulum-chain/spacewalk](https://github.com/pendulum-chain/spacewalk), you'll see that the repository is structured as follows this:

* **clients** -> contains the runtime and [vault's](broken-reference) logic needed to perform the vault operations
* **pallets** -> contains the actual Spacewalk pallet
* **testchain** -> a simple standalone chain that includes and makes use of the pallet

### Run the Testnet

We can start testing by running the following commands:

```
git clone git@github.com:pendulum-chain/spacewalk.git
cd spacewalk
git checkout main
cargo run --release -- --dev
```

The last command will compile the _testchain_ and the _pallet_ as well, and then it will run the testnet on `localhost:9944`.

It may take a while to build it the first time so if you already did this step before and you only want to run the testnet, just do:

```bash
./target/release/spacewalk-standalone --dev
```

**Note:** If you only want to build or test the pallet itself, you could of course navigate to `pallets/spacewalk` and run `cargo build`, or `cargo test.`
