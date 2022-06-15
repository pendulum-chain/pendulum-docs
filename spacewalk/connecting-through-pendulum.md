# Connecting through pendulum

There are a number of ways to interact with spacewalk.  In addition to our testchain, the spacewalk pallet is integrated into Pendulum.  By running a local testchain with a pendulum collator, the same process of creating stellar test accounts can be performed on your local chain.  Steps for running a local pendulum chain are provided [here](../build/running-pendulum-locally/) and steps for doing so with pendulum-launch are provided [here](../build/using-pendulum-launch/).

Once you have a running parachain, the same steps of creating test accounts and running the vault client can be performed; however, when running the vault client, it is necessary to include additional flags. &#x20;

Since the url of our parachain's exposed websocket may differ from the default used in the testchain, it is necessary to pass the correct url using the `--spacewalk-parachain-url` flag,  where the url is the address of the exposed websocket on your pendulum collator node.

{% hint style="info" %}
ex: `--spacewalk-parachain-url ws://localhost:8844`
{% endhint %}

We'll additionally need to enable the `parachain-metadata-testnet` feature, in place of the `standalone-metadata` feature.  The updated command for running the vault client against your local pendulum chain would look as follows.

```
cargo run --bin vault --features parachain-metadata-testnet -- --keyring alice --spacewalk-parachain-url <parachain-url> --stellar-vault-secret-key <vault-secret>
```
