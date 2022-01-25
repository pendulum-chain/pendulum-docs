# Local relay chain setup

### Prerequisites

Clone the polkadot repository

```
git clone
```

and download the raw `rococo-custom-2-raw.json` chain-spec file [here](https://docs.substrate.io/assets/tutorials/cumulus/chain-specs/rococo-custom-2-raw.json) and put in in the root of the cloned `polkadot` repository.

### Running the relay chain validators

From inside the cloned `polkadot` repository

**Run relay-chain validator 1**

```
./target/release/polkadot \
--alice \
--validator \
--base-path /tmp/relay/alice \
--chain ./rococo-custom-2-raw.json \
--port 30333 \
--ws-port 9944
```

**Check the logs for the node identity of alice (see line 4)**

```
...
⏱ Loaded block-time = 6s from block 0x7035c844a493bb0324763d592fa3dec2ca68ee0d88ad0513e322e02a209e625e
👶 Creating empty BABE epoch changes on what appears to be first startup.
🏷 Local node identity is: 12D3KooWMXKd3SybDBuDC8zLbSxzjy7dSNz9gvumFbkxoUEJY4H3
📦 Highest known block at #0Run relay-chain validator 2
...
```

**Run relay-chain validator 2**

```
./target/release/polkadot \
--bob \
--validator \
--base-path /tmp/relay/bob \
--chain ./rococo-custom-2-raw.json \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/<Alice_NODE_ID> \
--port 30334 \
--ws-port 9945
```





