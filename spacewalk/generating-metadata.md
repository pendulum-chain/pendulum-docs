---
description: >-
  This page describes how to generate a metadata scale file manually from your
  parachain in order to execute the Vault properly.
---

# Generating metadata

The metadata file is used by the Vault client in order to interact with the Substrate Chain, \
since it contains all the extrinsics and events that are used by it.\
There are many tools that can be used to fetch this file, namely [subxt](https://github.com/paritytech/subxt) from Parity among others, but here we will focus on how to do it without them. \
\
First of all, it is really important that we get this file from the chain we are connecting to. If your adding the pallet to a Parachain, then make sure you extract the metadata from the collator node.

{% hint style="danger" %}
When connecting to a parachain, make sure to write down the ws port in which the collator node listening to.

Even though you might have specified the port with `--ws-port`when launching the collator node, if it conflicts with a port already in use, a random one would be used instead.
{% endhint %}

Once the node is running, we need to send a `jsonrpc` call to it and execute the \
`state_getMetadata` extrinsic. So find your favorite tool for connecting to a websocket (eg. [Postman](https://www.postman.com/)), and send the following request to \
`ws://localhost:{your_node_port}`:&#x20;

```
{  
    "id": 1,  
    "jsonrpc": "2.0",  
    "method": 
    "state_getMetadata",  
    "params": []
}
```

If successful, this would give you a result similar to this one:

```
{  
    "jsonrpc": "2.0",  
    "result": "0x6d6574610b7c1853797374656d3a3a4163..."
    "id": "1"
}
```

Copy the resulting hex to a file and save it.&#x20;

Now, we need to process that file i.e. convert it into bytes representation and save it as `metadata-standalone.scale`.\
\
Here is a piece of Rust code that will do it for you. Replace the filename in the code to match your file and run it.

```
fn main() {
    // replace metadata.txt with your file's name 
    let content = fs::read_to_string("./metadata.txt").expect("Unable to read file");

    let bytes = hex::decode(content.trim_start_matches("0x")).unwrap();

    std::io::stdout().write_all(&bytes).unwrap();
}
```

Now with this, run the project and pipe the output to a file\
`cargo run --release > metadata-standalone.scale`\
\
Now that we have the scale file, you need to copy it to `clients/runtime/metadata-standalone.scale` , since it will be used later when running the vault.
