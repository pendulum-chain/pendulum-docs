# Techincal FAQ

**What is the required disk size to run the chain?**

250-500GB per node - <200GB (Polkadot) + 5GB (Pendulum) and increasing.

**Block data of mainnet or snapshots**

We currently don't have a snapshot available. Any node would need to sync from scratch but that would not take long as Pendulum just started recently. You can use [https://dot-rocksdb.polkashots.io/](https://dot-rocksdb.polkashots.io/) to speed up the sync of the relay chain embedded node.

**What is the block producing rate?**

12s

**What is the precision of each transaction**

12 Decimals

**How to create an account?**

This is for polkadot → [https://support.polkadot.network/support/solutions/articles/65000098878-how-to-create-a-dot-account](https://support.polkadot.network/support/solutions/articles/65000098878-how-to-create-a-dot-account)&#x20;

As Pendulum is a polkadot parachain, the account would also be created for Pendulum in the above process.

**Where tdo I find the configuration file directory?**

[https://github.com/pendulum-chain/pendulum/blob/main/runtime/pendulum/src/lib.rs](https://github.com/pendulum-chain/pendulum/blob/main/runtime/pendulum/src/lib.rs)

**How to customize RPC Port and directory of block data?**

Please follow our guideline for setting up an RPC or collator node, which should implicitly contain this information ([https://pendulum.gitbook.io/pendulum-docs/build/node-operators/collators/set-up-collator](https://pendulum.gitbook.io/pendulum-docs/build/node-operators/collators/set-up-collator))

`--rpc-port` is the parameter for RPC port and `-d` is the directory for data. You can access the documentation on node parameters here: [https://docs.substrate.io/reference/command-line-tools/node-template/](https://docs.substrate.io/reference/command-line-tools/node-template/)

**More API instructions?**

[https://polkadot.js.org/docs/api/start](https://polkadot.js.org/docs/api/start)&#x20;

**How do you prevent forking?**

This does not happen as the Polkadot relay chain does the consensus for the Pendulum parachain. So the measures to avoid this are the measures employed for Polkadot.

**How to restore and recover accounts?**&#x20;

This is the document on how to recover account → ​​[https://support.polkadot.network/support/solutions/articles/65000169952-polkadot-extension-how-to-restore-your-account](https://support.polkadot.network/support/solutions/articles/65000169952-polkadot-extension-how-to-restore-your-account)&#x20;

**How does the networks avoid 51% attack?**

The parachains are secured by the massive relay chain and don't execute their own consensus protocol. Read more here [https://wiki.polkadot.network/docs/learn-consensus#nominated-proof-of-stake](https://wiki.polkadot.network/docs/learn-consensus#nominated-proof-of-stake)&#x20;

**Will there be rollbacks?**

There can't be a rollback because our consensus happens on the Polkadot relay chain

**Is there a timeout mechanism for a transaction in tx pool, and if so, how long does it deal?**

Every transaction has an optional expiry time. After that they will be removed from the pool.





\
