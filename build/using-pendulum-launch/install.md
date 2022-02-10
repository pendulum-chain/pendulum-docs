---
description: In this section we discuss installing pendulum-launch
---

# 🐛 Install

### Prerequisites

* Cargo
* Git

For the purpose of this documentation, we will assume all binaries be moved into the main repository's `./bin` directory.



We will first clone and build the launcher

```
git clone https://github.com/pendulum-chain/pendulum-launch
cd pendulum-launch
cargo build --release
```



We will additionally want to build our collators and/or validators.  In this example we use [polkadot](https://github.com/paritytech/polkadot) as our validator node and [pendulum](https://github.com/pendulum-chain/pendulum) as our collator node.

```
git clone https://github.com/paritytech/polkadot
cd polkadot
cargo build --release
```

```
git clone https://github.com/pendulum-chain/pendulum
cd pendulum
cargo build --release
```
