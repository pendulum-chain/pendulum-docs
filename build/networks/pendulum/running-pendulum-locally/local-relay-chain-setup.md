# Local relay chain setup

### Prerequisites

First, clone the [polkadot repository](https://github.com/paritytech/polkadot):

```
git clone https://github.com/paritytech/polkadot.git
```

Then, download the raw `raw-local-chainspec.json` chain-spec file [here](https://docs.substrate.io/assets/tutorials/relay-chain-specs/raw-local-chainspec.json/) and put it in the root of the cloned `polkadot` repository.

At the time of writing this, the Pendulum parachain is using Polkadot dependencies of version `v0.9.29`. So for compatibility purposes, you need to check out the respective branch before building the node.

```
# Checkout correct branch
git checkout release-v0.9.29
# Build polkadot node
cargo build --release
```

### Running the relay chain validators

From inside the cloned `polkadot` repository (after building the node):

**Run relay-chain validator 1**

```
./target/release/polkadot \
--alice \
--validator \
--base-path /tmp/relay/alice \
--chain ./raw-local-chainspec.json \
--port 30333 \
--ws-port 9944
```

If you ran this validator before and you would like to start afresh from genesis, then you would need to remove the folder `/tmp/relay` first (and similarly for the following validator and collator nodes in this tutorial).

**Check the logs for the node identity of Alice (see line 4) and copy it to your clipboard**

```
...
⏱ Loaded block-time = 6s from block 0x7035c844a493bb0324763d592fa3dec2ca68ee0d88ad0513e322e02a209e625e
👶 Creating empty BABE epoch changes on what appears to be first startup.
🏷 Local node identity is: 12D3KooWMXKd3SybDBuDC8zLbSxzjy7dSNz9gvumFbkxoUEJY4H3 # COPY THIS ID
📦 Highest known block at #0Run relay-chain validator 2
...
```

**Run relay-chain validator 2 (with copied node ID)**

```
./target/release/polkadot \
--bob \
--validator \
--base-path /tmp/relay/bob \
--chain ./raw-local-chainspec.json \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/<Alice_NODE_ID> \ # REPLACE ME WITH COPIED ID
--port 30334 \
--ws-port 9945
```
