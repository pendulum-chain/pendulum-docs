---
description: Common errors and how to solve them
---

# Troubleshooting

### The relay chain is not producing new blocks&#x20;

If you can't see the relay chain or parachain producing new blocks, check the logs of your commands.

Make sure that both collator nodes are running because if only one is running no new blocks will be produced.

Also double-check that you changed the `<ALICE_NODE_ID>` in the `--boot-nodes` command when running Bob. Otherwise, the Bob collator might not find Alice.&#x20;

#### macOS users

On macOS, it might help to temporarily disable the firewall in the system settings. This way you are not required to use the `--boot-nodes` parameter and the validator and collator nodes should be able to find each other without it.

### The parachain is not producing new blocks

Check if the relay chain validators are producing new blocks. If they are, check if the parachain is registered in the parachains tab.&#x20;

### Error: "Unexpected epoch change"

If you see something like `Error with block built on 0x...: ClientImport("Unexpected epoch change")` the easiest solution is to delete the files in the temporal directory.&#x20;

The directory you have to delete is indicated with `--base-path` in the previous command blocks. By default it would be `/tmp/relay/` so you would do `rm -rf /tmp/relay`
