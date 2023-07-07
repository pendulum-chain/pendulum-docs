# Getting Started

## Operating a Vault

The Spacewalk vault client intermediates between the Stellar network and the Spacewalk-chain.

### Prerequisites

* A recent version of Linux or MacOS. Windows support is not tested.
* At least 2 GB of RAM and a good CPU - exact requirements not yet benchmarked.
* Free disk space (ideally SSD):
  * at least **30 GB** if you build the vault client binary from sources
  * at least **10 GB** if you use a pre-built binary
* A stable internet connection.
* At least 1 PEN/AMPE to pay for initial transaction fees.

## Before Building

Make sure you have completed the basic Rust setup, see [here](https://github.com/pendulum-chain/spacewalk/blob/main/testchain/docs/rust-setup.md) for more information

## Installation

### Install a pre-built binary

At the moment, we only offer pre-built binaries for Ubuntu Linux operating systems. You can download the latest binary from our releases [here](https://downloads.pendulumchain.tech/index.html). Then change the file permission to make it executable.

### Install from source

If there is no pre-built binary available for your operating system, you can install and build the vault client from scratch.&#x20;

{% hint style="danger" %}
Building from source requires \`clang 11\`. Make sure to check this via \`clang -v\`.
{% endhint %}

#### Install Rust

```json
curl https://sh.rustup.rs -sSf | sh
```

#### Build the Vault client

Clone the Vault code, checkout the latest release and build the client:

```bash
git clone https://github.com/pendulum-chain/spacewalk.git
cd spacewalk
git checkout master
cargo build --bin vault --features parachain-metadata-<parachain> --release
```

Where \<parachain> is one of the following:

* `foucoco` (Rococo / test network)
* `amplitude` (Kusama / canary network)
* `pendulum` (Polkadot / Mainnet)

## Usage

The `--stellar-vault-secret-key-filepath` and `--stellar-overlay-config-filepath` parameters are mandatory. The other parameters are optional and have default values.

Depending on whether you build the vault client from source or downloaded a binary from the release page, the path to your executable might vary.&#x20;

A simple example of running a vault client that connects to the Foucoco network could be:

```bash
<path-to-binary> \  
  --auto-register 0,GAKNDFRRWA3RPWNLTI3G4EBSD3RGNZZOY5WKWYMQ6CQTG3KIEKPYWAYC:USDC,100000000000000 \ 
  --keyfile keys.json \
  --keyname my-key \
  --spacewalk-parachain-url wss://rpc-foucoco.pendulumchain.tech:443 \
  --stellar-vault-secret-key-filepath secret_key_foucoco \
  --stellar-overlay-config-filepath clients/stellar-relay-lib/resources/config/testnet/stellar_relay_config_sdftest1.json
```

This command will make the vault client auto-register itself for the asset pair KSM<-> USDC, providing collateral of `100_000_000_000_000` which is 100 KSM. The vault will try to use the key named `my-key` contained in the `keys.json` file as its account on the Spacewalk-chain. The secret key for the vault's Stellar account is contained in a file called `secret_key_foucoco` .&#x20;

Logging can be configured using the [RUST\_LOG](https://docs.rs/env\_logger/0.8.3/env\_logger/#enabling-logging) environment variable. By default, the Vault will log at `info` or above but you may, for example, configure `debug` logs for increased verbosity.

## Options

You can run the vault with the following parameters:

`-h, --help` - Print help information

`-V, --version` - Print version information

`--auto-register <AUTO_REGISTER>` - Automatically register the vault with the given amount of collateral. The format of the `<AUTO_REGISTER>` parameter is `COLLATERAL_CURRENCY,WRAPPED_CURRENCY,COLLATERAL` . \
The currencies can be of the following format:

* `<u8>` - A simple number, depicting the index of the XCM currency ID. At the moment, the only supported XCM currency is the native currency of the respective relay chain, ie. $DOT or $KSM. To use $DOT or $KSM, use `0`.
* `XLM` - representing the native token of the Stellar network
* `<ASSET_ISSUER>:<ASSET_CODE>` - this combination is used to uniquely identify assets on Stellar. The `ASSET_ISSUER` is the public key of the asset's issuer, and `ASSET_CODE` is the identifier of the asset.

For example, to auto-register the vault for providing collateral of `1` DOT for the Stellar USDC issued by [centre.io](http://centre.io) you would use

```bash
--auto-register="0,GA5ZSEJYB37JRC5AVCIA5MOP4RHTM335X2KGX3IHOJAPP5RE34K4KZVN:USDC,10000000000" \
```

`--stellar-vault-secret-key <STELLAR_VAULT_SECRET_KEY>` - The Stellar secret key that is used by the vault to sign transactions and receive user assets on Stellar.

`--stellar-overlay-config-filepath <STELLAR_OVERLAY_CONFIG_FILEPATH>` - The file path to where the JSON config for the Stellar overlay network is located. This is important because the vault client needs to know where to find the consensus-related information. You can find an example for this file [here](https://github.com/pendulum-chain/spacewalk/blob/67f3b695a098be4ad687dc3df575204d9b214475/clients/stellar-relay-lib/resources/config/mainnet/stellar\_relay\_config\_mainnet\_iowa.json).

`--keyfile <KEYFILE>` - Path to the json file containing key pairs in a map. Valid content of this file is e.g.

```json
{ "MyUser1": "<Polkadot Account Mnemonic>", "MyUser2": "<Polkadot AccountMnemonic>" }`
```

`--keyname <KEYNAME>` - The name of the account from the `keyfile` to use

`--keyring <KEYRING>` - The keyring to use, e.g. ‘ALICE’. Mutually exclusive with `keyfile`. This is more useful for testing purposes.

`--no-auto-replace` - Opt out of participation in replace requests

`--no-issue-execution` - Don't try to execute issues

`--payment-margin-minutes <PAYMENT_MARGIN_MINUTES>` - Minimum time to the redeem/replace execution deadline to make the stellar payment \[default: 1]. If requests are too close to the deadline the vault might not be able to complete them in time due to network latency, etc.

`--restart-policy <RESTART_POLICY>` - Restart or stop on error \[default: always]. Possible `RESTART_POLICY`s are ‘always’ and ‘never’.

`--spacewalk-parachain-connection-timeout-ms <SPACEWALK_PARACHAIN_CONNECTION_TIMEOUT_MS>` - Timeout in milliseconds to wait for the connection to the spacewalk-parachain \[default: 60000]

`--spacewalk-parachain-url <SPACEWALK_PARACHAIN_URL>` - Parachain websocket URL. \[default is `ws://127.0.0.1:9944`]. At the moment, the parachain URL should be one of the following:

* `wss://rpc-foucoco.pendulumchain.tech:443` - Foucoco
* `wss://rpc-amplitude.pendulumchain.tech:443` - Amplitude
* `wss://rpc-pendulum.prd.pendulumchain.tech:443` - Pendulum

`--logging-format <LOGGING_FORMAT>` - Logging output format \[default: full]. `LOGGING_FORMAT` can be “json” or “full”.

`--max-concurrent-requests <MAX_CONCURRENT_REQUESTS>` - Maximum number of concurrent requests

`--max-notifs-per-subscription <MAX_NOTIFS_PER_SUBSCRIPTION>` - Maximum notification capacity for each subscription.

`--faucet-url <FAUCET_URL>` - Pass the faucet URL for auto-registration. Not yet supported.

## Do's and Don'ts

Operating a Vault client at the current stage involves running a fully automated client on a server. This client has access to hot wallets for both Stellar and the Pendulum networks. The setup below is - on purpose - technically challenging to minimize the chance that Vaults and users lose funds due to operation errors.

When operating a Vault client ensure the following:

1. **Do NOT operate two or more Vault clients with the same keyname/account at the same time.** The Vault stands the risk to execute redeem transactions twice which will lead to a loss of Assets - and, in the worst case, liquidation of collateral.
2. **DO restricts access to your server.** If anyone has access to your server, they will be able to extract any funds present. Make sure to close any unnecessary ports to third parties.
3. **DO backup your keys.** If the keys are not backed-up and the server operating the Vault client loses this data, the Vault stands the risk of losing all funds.&#x20;
4. **DO monitor the Vault for potential failures.** This includes three parts: (1) keeping the collateralization level above the liquidation threshold, (2) fulfilling redeem requests on time, (3) ensuring that you have enough Assets in the Vault’s wallet to fulfill redeem requests.&#x20;

## Troubleshooting

This is a list of known issues that you might face while installing the Spacewalk Client

#### Invalid spec version

If there are errors with spec versions not matching you might have to change the `DEFAULT_SPEC_VERSION` in runtime/src/rpc.rs.

#### Building on macOS

If you are encountering build errors on macOS try the following steps:

1. Install llvm with brew (`brew install llvm`).
2. Install wasm-pack for cargo (`cargo install wasm-pack`).
3. Set clang variables

```
# on intel CPU
export AR=/usr/local/opt/llvm/bin/llvm-ar
export CC=/usr/local/opt/llvm/bin/clang
# on M1 CPU
export AR=/opt/homebrew/opt/llvm/bin/llvm-ar
export CC=/opt/homebrew/opt/llvm/bin/clang
```

#### Transaction submission failed

If the transaction submission fails giving a `tx_failed` in the `result_codes` object of the response, this is likely due to the converted destination account not having trustlines set up for the redeemed asset. The destination account is derived automatically from the account that called the extrinsic on-chain.

###

\
