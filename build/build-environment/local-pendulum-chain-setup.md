---
description: Before running the test chain locally you need to be run the relay chain!
---

# Local Pendulum chain setup

### Prerequisites

First, you need to clone the Pendulum repository.&#x20;

```
git clone https://github.com/pendulum-chain/pendulum.git
```

Then compile the project executing

```
cargo build --release
```

### Reserving a para ID

Connect to the relay chain using [this](https://polkadot.js.org/apps/?rpc=ws%3A%2F%2F127.0.0.1%3A9944#/parachains/parathreads) link. Reserve a parachain slot for ID 2000 by clicking on the button "+ ParaId".

### Leasing a slot for the parachain on the relay chain

To run and connect your parachain collator to the relay chain you first need to generate some files. Run the following commands from the root of the `pendulum` repository:

First generate a plain chain spec of your parachain:

```
# Generate a plain chain spec of your parachain
./target/release/pendulum-collator build-spec --disable-default-bootnode > rococo-local-parachain-plain.json
```

By default, the para ID in the generated `rococo-local-parachain-plain.json` is set to `1000`. But in the step earlier, we reserved a parachain slot for ID `2000`. That's why you will have to manually change the contents of the generated JSON file to match the setup of your leased parachain ID. For more information, see the [Substrate docs](https://docs.substrate.io/tutorials/v3/cumulus/connect-parachain/#configure-a-parachain-for-a-specific-relay-chain-and-para-id).  You have to modify two fields, similar to this snippet:

```
// --snip--
  "para_id": 2000, // <--- your already registered ID
  // --snip--
      "parachainInfo": {
        "parachainId": 2000 // <--- your already registered ID
      },
  // --snip--
```

Afterwards, you can generate the other necessary files with the following commands:

```
# Generate a raw chain spec derived from the plain chain spec
./target/release/pendulum-collator build-spec --chain rococo-local-parachain-plain.json --raw --disable-default-bootnode > rococo-local-parachain-2000-raw.json

# Generate the WASM runtime validation function
./target/release/pendulum-collator export-genesis-wasm --chain rococo-local-parachain-2000-raw.json > para-2000-wasm

# Generate a parachain genesis state
./target/release/pendulum-collator export-genesis-state --chain rococo-local-parachain-2000-raw.json > para-2000-genesis
```

These commands generate the following files:&#x20;

* rococo-local-parachain-2000-plain.json
* rococo-local-parachain-2000-raw.json
* para-2000-genesis
* para-2000-wasm

Use the first option described [here](https://docs.substrate.io/tutorials/v3/cumulus/connect-parachain/#register-using-sudo) to create a slot for your parachain. After submitting the sudo transaction you have to wait until the 'onboarding' is completed and your parachain is fully connected to the relay chain. You can check the remaining time estimate of the onboarding process [here](https://polkadot.js.org/apps/?rpc=ws%3A%2F%2F127.0.0.1%3A9944#/parachains/parathreads).&#x20;

Once the process has finished, you should be able to see your parachain in the [parachains](https://polkadot.js.org/apps/?rpc=ws%3A%2F%2F127.0.0.1%3A9944#/parachains) tab.

### **Run parachain collator**

Copy your `rococo-custom-2-raw.json` file that you downloaded in the previous step to the root of the `pendulum` project.

Run the following command but replace `<ALICE_NODE_ID>` with the node Identity of one of the validators that you started in the previous chapter. It doesn't matter if you use Alice's or Bob's ID.

```
./target/release/pendulum-collator \
--alice \
--rpc-cors=all \
--collator \
--force-authoring \
--chain rococo-local-parachain-2000-raw.json \
--base-path /tmp/parachain/alice \
--port 40333 \
--ws-port 8844 \
--enable-offchain-indexing TRUE \
-- \
--execution wasm \
--chain ./rococo-custom-2-raw.json \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/<ALICE_NODE_ID> \
--port 30343 \
--ws-port 9977

```

{% hint style="info" %}
The `--bootnodes` parameter is used to make sure that the parachain collator finds the peers of the relay chain. You can see if the relay chain peers are found in the logs. It should read something like`[Relaychain] Idle (2 peers)...`
{% endhint %}

```
[Relaychain] 💤 Idle (2 peers), best: #22 (0xf4fc…7c5e), finalized #19 (0x561e…9ced), ⬇ 1.0kiB/s ⬆ 0.7kiB/s    
[Parachain] 💤 Idle (0 peers), best: #0 (0x1249…11f9), finalized #0 (0x1249…11f9), ⬇ 0 ⬆ 0    
[Relaychain] ✨ Imported #23 (0xe86a…a30f)
```

### Interacting with the parachain

After some minutes the collator node of the parachain will start to produce blocks. This is easiest to identify on the polkadot.js explorer. First identify the websocket port of the collator node. This is `8844` by default but can deviate occasionally. For this purpose check the line `Listening for new connections on 127.0.0.1:<ws-port>` in the console output.

Expand the sidebar of the polkadot.js explorer and enter `ws://localhost:<ws-port>` as "Custom Endpoint" below the "Development" area or alternatively use [this](https://polkadot.js.org/apps/?rpc=ws%3A%2F%2Flocalhost%3A8844#/explorer) link to directly access the page with the endpoint filled in for you. After that head to "Network -> Explorer" and you should be able to see that the parachain is producing blocks.
