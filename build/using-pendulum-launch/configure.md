---
description: In this section we discuss writing a configuration file
---

# ⚙ Configure



pendulum-launch is configured with a JSON file, the default location for which being the root directory of your repository.  Paths in the config are relative to the current working directory, so configs in non-default directories will need to assume paths relative to where the launcher is being used, not where the config is.

### example.json

```json5
{
  "name": "Pendulum",
  "author": "xiuxiu",
  "validators": [
    {
      "name": "validator_node",
      "bin": "./bin/polkadot",
      "chain": "./specs/rococo-custom-2-raw.json",
      "args": [],
      "port": 30343,
      "ws_port": 9944,
      "rpc_port": 10000
    }
  ],
  "collators": [
    {
      "inner": {
        "name": "collator_node",
        "bin": "./bin/pendulum-collator",
        "chain": "./specs/rococo-local-parachain-raw.json",
        "args": ["--force-authoring", "--enable-offchain-indexing", "true"],
        "port": 30344,
        "ws_port": 8844,
      },
      "relay": {
        "chain": "./specs/rococo-custom-2-raw.json",
        "args": ["--force-authoring"],
        "port": 30345,
        "ws_port": 9955,
      }
    }
  ]
}
```

As seen above, the network is defined by a list of validators and collators.  Each node must provide path's to their binary and chain specification file, as well as a node port and websocket port.  RPC ports are optional.  While validator and collator lists are not optional, you can leave either of them empty if you do not wish to launch one or the other.
