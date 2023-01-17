# Running the vault

The second important block of our testing scenario are the _**vaults**_. These take care of fetching information from Stellar and reporting it to the _testchain_, as well as reacting to certain events on the _testchain_ and forwarding them to Stellar.

For running the vault, be sure you have copied the secret key of the Vault Account you created in the [previous step](creating-test-accounts.md). Then run the following command and replace `<vault-secret>` with the secret key:

```bash
cd clients
cargo run --bin vault --features standalone-metadata -- --keyring alice --stellar-vault-secret-key <vault-secret>
```

Wait until it finishes building, and ignore any warnings. If it builds and runs successfully, you should see logs like this:

![](../../../.gitbook/assets/vaultlogs)

At this point, you have the main blocks up and running, and you're ready to bridge some assets.
