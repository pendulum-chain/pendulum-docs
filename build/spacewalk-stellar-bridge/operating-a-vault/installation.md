# Installation

## Operating a Vault

The Spacewalk vault client intermediates between Stellar and the Pendulum parachain.

### Prerequisites

* A recent version of Linux or MacOS. Windows support is not tested.
* At least 2 GB of RAM and a good CPU - exact requirements not yet benchmarked.
* Free disk space (ideally SSD):
  * at least **30 GB** if you build the vault client binary from sources
  * at least **10 GB** if you use a pre-built binary
* A stable internet connection.
* At least 1 PEN/AMPE to pay for initial transaction fees.

## Installation

### Install a pre-built binary

Download the respective asset for your operating system from our GitHub [releases](https://github.com/pendulum-chain/spacewalk/releases) page.

Then change the file permission to make it executable.

### Install from source

{% hint style="danger" %}
Building from source requires \`clang 11\`. Make sure to check this via \`clang -v\`.
{% endhint %}

#### Install Rust

```json
curl https://sh.rustup.rs -sSf | sh
```

#### Build the Vault client

Clone the Vault code, checkout the release and build the client:

```bash
git clone https://github.com/pendulum-chain/spacewalk.git
cd spacewalk
git checkout master
cargo build --bin vault --features parachain-metadata
```

#### Start the Vault client

Move the vault binary into your `$PATH`.

To start the client, you can connect to our parachain full node. You can find more information on the available parameters and their usages below.

```bash
vault \
  --keyfile keyfile.json \
  --keyname <YOUR_KEYNAME> \
  --auto-register="DOT,GABC...XYZ:USDC,1000000000000000000" \
  --auto-register="DOT,GABC...XYZ:MXN,1000000000000000000" \
  --spacewalk-parachain-url 'wss://rpc-amplitude.pendulumchain.tech:443'
```

Logging can be configured using the `[RUST_LOG](https://docs.rs/env_logger/0.8.3/env_logger/#enabling-logging)` environment variable. By default, the Vault will log at `info` or above but you may, for example, configure `debug` logs for increased verbosity.

## Usage

You can run the vault with the following parameters. The `--stellar-vault-secret-key` parameter is mandatory, the other parameters are optional and have default values.

### Options

`-h, --help` Print help information

`-V, --version` Print version information

`--auto-register <AUTO_REGISTER>` Automatically register the vault with the given amount of collateral. The format of the `<AUTO_REGISTER>` parameter is `COLLATERAL_SYMBOL,ASSET_ISSUER:ASSET_CODE,COLLATERAL` with `COLLATERAL_SYMBOL` being the Token symbol of the currency to use for collateral, `ASSET_ISSUER` being the public key and `ASSET_CODE` being the code of the issuing account of the bridged Stellar asset and `COLLATERAL` being the amount that is to-be-provided by the vault as collateral in the smallest possible unit. For example, to auto-register the vault for providing collateral of `1` DOT for the Stellar USDC issued by [centre.io](http://centre.io) you would use

```bash
  --auto-register="DOT,GA5ZSEJYB37JRC5AVCIA5MOP4RHTM335X2KGX3IHOJAPP5RE34K4KZVN:USDC,10000000000" \
```

`--stellar-vault-secret-key <STELLAR_VAULT_SECRET_KEY>` The Stellar secret key that is used by the vault to sign transactions and receive user assets on Stellar.

`--keyfile <KEYFILE>` Path to the json file containing key pairs in a map. Valid content of this file is e.g.

```json
{ "MyUser1": "<Polkadot Account Mnemonic>", "MyUser2": "<Polkadot AccountMnemonic>" }`
```

`--keyname <KEYNAME>` The name of the account from the `keyfile` to use

`--keyring <KEYRING>` The keyring to use, e.g. ‘ALICE’. Mutually exclusive with `keyfile`. This is more useful for testing purposes.

`--no-auto-replace` Opt out of participation in replace requests

`--no-issue-execution` Don't try to execute issues

`--payment-margin-minutes <PAYMENT_MARGIN_MINUTES>` Minimum time to the the redeem/replace execution deadline to make the stellar payment \[default: 1]. If requests are too close to the deadline the vault might not be able to complete them in time due to network latency, etc.

`--restart-policy <RESTART_POLICY>` Restart or stop on error \[default: always]. Possible `RESTART_POLICY`s are ‘always’ and ‘never’.

`--spacewalk-parachain-connection-timeout-ms <SPACEWALK_PARACHAIN_CONNECTION_TIMEOUT_MS>` Timeout in milliseconds to wait for the connection to the spacewalk-parachain \[default: 60000]

`--spacewalk-parachain-url <SPACEWALK_PARACHAIN_URL>` Parachain websocket URL. \[default is `ws://127.0.0.1:9944`]

`--logging-format <LOGGING_FORMAT>` Logging output format \[default: full]. `LOGGING_FORMAT` can be “json” or “full”.

`--max-concurrent-requests <MAX_CONCURRENT_REQUESTS>` Maximum number of concurrent requests

`--max-notifs-per-subscription <MAX_NOTIFS_PER_SUBSCRIPTION>` Maximum notification capacity for each subscription.

`--faucet-url <FAUCET_URL>` Pass the faucet URL for auto-registration. Not yet supported.
