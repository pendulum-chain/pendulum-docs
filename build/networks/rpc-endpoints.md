# RPC Nodes

## Types of nodes

***

Glossary of the different type of nodes that are involved in a typical parachain configuration. Other types exist but are not listed.



For a full, in-depth, understanding of nodes, refer to the [Polkadot](https://wiki.polkadot.network/docs/learn-architecture) Documentation

#### **Bootnodes**

A node with a static address and p2p public key, used to bootstrap a node onto the network’s distributed hash table and find peers.

#### **RPC endpoints**

Expose an RPC interface over http or websocket for the relay chain or parachain and allow users to read the blockchain state and submit transactions (extrinsics). There are often multiple RPC nodes behind a load balancer.

#### **Validators**

Secures the Relay Chain by staking DOT, validating proofs from collators on parachains and voting on consensus along with other validators.

#### **Collators**

Maintains a parachain by collecting parachain transactions and producing state transition proofs for the validators.

#### **Archives**

A node which is syncing to the relay chain or parachain and has a complete database starting all the way from the genesis block .

#### **Full node**

A node which is syncing the relay chain or parachain to the current best block.



## Nodes naming convention

***

The node's naming convention is as follows:

```bash
<prefix><type>-<network>-<number>
```

Where:

* `prefix` is always **pen**
* `type` can be any of **boot** | **col** | **val** | **rpc**
* `network` can be any of **roc** | **kus**
  * If the node is an archive, the network gets modified to: **roa** | **kua**
* `number` numerical order of the nodes of the same type



Example:

**penval-roc**-**00**

**pen** = pendulum

**val** = validator

**roc** = rococo

**00** = number of the node

