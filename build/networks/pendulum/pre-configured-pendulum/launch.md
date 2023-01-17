---
description: In this section we discuss using pendulum-launch to launch a parachain.
---

# Launch

The following command details how pendulum-launch is used.  The `--config` option can be used to set the path of a config file.  The `--log` option can be used to set an alternate logging directory.

{% hint style="info" %}
`pendulum-launch help`
{% endhint %}

```
pendulum-launch 0.2.0

USAGE:
    pendulum-launch [FLAGS] [OPTIONS] [SUBCOMMAND]

FLAGS:
    -h, --help       Prints help information
    -q, --quiet
    -V, --version    Prints version information

OPTIONS:
    -c, --config <config>
    -l, --log <log>

SUBCOMMANDS:
    export-genesis     Export genesis data
    generate-docker    Generate docker-compose.yml
    generate-specs     Generate specs
    help               Prints this message or the help of the given subcommand(s)
```

As an example, we might want to launch our parachain as follows `./bin/pendulum-launch --config ./launch-local.json --log ./tmp/local` in order to provide an alternate config and log directory.

## Launching a local Pendulum chain

### Prerequisites

To launch a local parachain you have to run a multitude of commands.

First, build the parachain-collator binary. From the **root directory of your parachain** (in this case pendulum) run:

```
cargo build --release
```

The next steps assume that you are in the **root directory of the pendulum-launch repository.**

Next, use pendulum-launch to generate the chain specs.

```
# Generate specs for parachain with ID 2000 and export to ./specs directory
./target/release/pendulum-launch generate-specs -n rococo-local-parachain -i 2000 -o ./specs/ ../pendulum/target/release/parachain-collator
```

With the chain spec, we can now export the genesis data.&#x20;

```
# Export genesis to local directory and export to ./specs directory
./target/release/pendulum-launch export-genesis -o ./specs ../pendulum/target/release/parachain-collator ./specs/rococo-local-parachain-raw.json
```

To run our setup we also need to have the binary of the [polkadot relay chain](https://github.com/paritytech/polkadot). If you don't want to compile it yourself you can download it from the [releases page](https://github.com/paritytech/polkadot/releases). Make sure you download the relay chain that works for the version of your parachain (i.e. if your parachain uses `polkadot-v0.9.17` dependencies, you should also download the corresponding relay chain).

### Launch the parachain

Now that we have all the prerequisites we need for running our Pendulum chain, we can use pendulum-launch to simultaneously run our relay-chain collators as well as our parachain validator.&#x20;

You can find the settings of both collators and validators in the `pendulum-launch/config/pendulum-launch.json` file. Check if the paths to the binaries are correct for your local setup. From the root directory of the pendulum-launch repository, run:

```
# Launch local setup based on supplied config
./target/release/pendulum-launch --config ./config/pendulum-launch.json 
```

Now you just need to register your parachain in the polkadot.js explorer, as is described [here](https://docs.substrate.io/tutorials/v3/cumulus/connect-parachain/#register-using-sudo). For `genesisHead` use the `pendulum-launch/specs/local-chain-state` file and for `validationCode` use the `pendulum-launch/specs/local-chain-wasm` file.

&#x20;You should see your parachain producing blocks after the onboarding is completed.
