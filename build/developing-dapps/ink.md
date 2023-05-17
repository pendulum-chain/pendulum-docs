# ink!

## What is ink!?

Parity's ink! is an extension of the popular Rust programming language, in this, it is an embedded domain-specific language (eDSL).\
It is an opinionated language developed with the focus on Smart Contracts for the Substrate framework

The smart contracts developed through ink! are compatible with the [Substrate Contracts Pallet](https://docs.substrate.io/tutorials/work-with-pallets/contracts-pallet/)

You can learn more about ink! on their [homepage](https://use.ink/) and on their [blog](https://www.parity.io/blog/what-is-paritys-ink)

## Convert Solidity to ink! smart contracts

{% hint style="info" %}
You can find more about Swanky [here](https://use.ink/getting-started/swanky/)
{% endhint %}

Swanky Suite is based on existing tools like `cargo contract CLI` and `polkadot.js` but extends their functionality with many additional features such as smart contract templates which reduces the contract development lifecycle.

You can use Swanky to convert your pre-built solidity contracts to ink!-compatible

### Setup

To begin with, install the swanky CLI tool:

```bash
npm install -g @astar-network/swanky-cli
```

With this done you can navigate to your project or start a new one. It is not needed to install swanky node for this process.

```bash
swanky init myproject
```

### Add Contract and update JSON

At this step you can update your code or simply use one of the preconfigured template. Once you are donem add the network you will be deploying to in `swanky.config.json:`

```json
"networks":{
// any other networks
// ...
"foucoco": {
      "url": "wss://pencol-roc-02.pendulumchain.tech:443"
    },
// ...
}
```

You will need a swanky account to deploy the contract

```
swanky account create
```

You can also test with a dev account and see the mnemonic being added to the JSON

```jsx
{
      "mnemonic": "foobarbaz",
      "isDev": true,
      "alias": "foobar",
      "address": "//anAddress"
    }
```

#### Add precompiled contracts to artifacts

If you have already compiled your contract using Solidity:

```
/artifacts/mycontract/timestamp/mycontract.contract
/artifacts/mycontract/timestamp/mycontract.json
```

**The main annoyance in this process is `mycontract.json` which needs to be created manually for precompiled contracts.** However, it appears it is expected to contain the exact same thing as the `mycontract.contract` minus the wasm key. &#x20;

#### Add contract to JSON

This would also be done automatically normally, but we have to manually supply this with precompiled contracts:\


```
  "contracts": {
    "mycontract": {
      "name": "mycontract",
      "deployments": [],
      "language": "ink",
      "build": {
        "timestamp": 1677065947958,
        "artifactsPath": "/Users/hugo/Code/myproject/artifacts/mycontract/1677065947958"
      }
    }
  },
```

### Deploy

Change the --network argument with the network you want to use, or use local for testing

```jsx
swanky contract deploy <yourContract> --account <yourAccount> --gas <Initial Gas> --args true --network local
```



## Known Issues

* If you are facing issues with cargo, you might need to first [install](https://github.com/paritytech/cargo-contract) `cargo contract`
* Facing error:

```jsx
✖ Error Getting WASM
```

check  your path in the JSON is correct!&#x20;

alternatively, verify the [logs](https://substrate.stackexchange.com/questions/6888/error-compling-contract), it might not be a swanky issue

