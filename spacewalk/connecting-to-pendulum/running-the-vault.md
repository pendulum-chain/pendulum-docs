# Running the vault

This step is similar to what's described for our testchain, only that you need to change some parameters.

Since the url of our parachain's exposed websocket may differ from the default used in the testchain, it is necessary to pass the correct url using the `--spacewalk-parachain-url` flag,  where the url is the address of the exposed websocket on your pendulum collator node.

{% hint style="success" %}
Use it like this:

`--spacewalk-parachain-url ws://localhost:{spacewalk_chain_port}`
{% endhint %}

We'll additionally need to enable the `parachain-metadata` feature, in place of the `standalone-metadata` feature.&#x20;

{% hint style="success" %}
The updated command for running the vault client against your local pendulum chain would look as follows.

`cargo run --bin vault --features parachain-metadata -- --keyring alice --spacewalk-parachain-url <parachain-url> --stellar-vault-secret-key <vault-secret>`
{% endhint %}
