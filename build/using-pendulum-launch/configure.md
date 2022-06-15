---
description: In this section we discuss writing a configuration file
---

# ⚙ Configure

pendulum-launch is configured with a JSON file, the default location for which being the root directory of your repository.  Paths in the config are relative to the current working directory, so configs in non-default directories will need to assume paths relative to where the launcher is being used, not where the config is.

### Example configuration

```json5
{
    "name": "Pendulum",
    "author": "xiuxiu",
    "mode": "local",
    "validator": {
        "bin": "./bin/polkadot",
        "dockerfile": "./tmp/Dockerfile",
        "nodes": [
            {
                "name": "validator_node",
                "chain": "./examples/specs/rococo-custom-2-raw.json",
                "args": ["--alice", "--base-path=/tmp/relay/alice"],
                "port": 30343,
                "ws_port": 9945,
                "rpc_port": null
            },
            {
                "name": "validator_node2",
                "chain": "./examples/specs/rococo-custom-2-raw.json",
                "args": ["--bob", "--base-path=/tmp/relay/bob"],
                "port": 30353,
                "ws_port": 9946,
                "rpc_port": null
            }
        ]
    },
    "collator": {
        "bin": "./bin/parachain-collator",
        "dockerfile": "./tmp/Dockerfile",
        "nodes": [
            {
                "name": "glitch-princess-1",
                "chain": "./examples/specs/local-chain-raw.json",
                "args": [
                    "--rpc-cors",
                    "all",
                    "--force-authoring",
                    "--enable-offchain-indexing",
                    "true"
                ],
                "port": 30344,
                "ws_port": 8844,
                "rpc_port": null,
                "relay": {
                    "chain": "./examples/specs/rococo-custom-2-raw.json",
                    "args": [
                        "--rpc-cors",
                        "all",
                        "--force-authoring"
                    ],
                    "port": 30345,
                    "ws_port": 9944,
                    "rpc_port": null
                }
            }
        ]
    }
}
```

As seen above, the network is defined by a list of validators and collators.  Each node must provide path's to their binary and chain specification file, as well as a node port and websocket port.  RPC ports are optional.  While validator and collator lists are not optional, you can leave either of them empty if you do not wish to launch one or the other.
