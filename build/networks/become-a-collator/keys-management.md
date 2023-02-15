# Keys Management

## Insert your Aura keys

While waiting for the node to finish syncing, you can already proceed with the next required step. This is about inserting an authority key pair to your node, i.e. a pair of private and public keys that will allow you to have control on the node, and it's required for the next step, where we will guide you through the staking and rewards configuration.

So, if you already own an account that you want to use, you can skip the next section. But if you still don't have a key pair already generated, let's first do that.

### Generating Aura keys

There are many ways of generating a new account or pair of keys. To stay secure, the best is to generate them offline using a tool called [subkey](https://docs.substrate.io/reference/command-line-tools/subkey/). You can follow the steps there in order to install it in your system.

Then, to generate the keys you simply run:

```
subkey generate
```

You'll get an output like:

```
Secret phrase:       rubber begin sail spider green hope two fetch immune nation connect swarm
  Network ID:        substrate
  Secret seed:       0xe691a1a17f124bc41ce59b4a4ae1343ac975dc98d5edb4fd68460cdbc2f1ef42
  Public key (hex):  0x422cf4ec55a544d31e6a1ecf21afe005f94373214b87be66c613d97e9db8ea18
  Account ID:        0x422cf4ec55a544d31e6a1ecf21afe005f94373214b87be66c613d97e9db8ea18
  Public key (SS58): 5DZUNZJr6nfMwgbx1MNijoEojkARa6mvS5nbnZHJ9EHWnhAq
  SS58 Address:      5DZUNZJr6nfMwgbx1MNijoEojkARa6mvS5nbnZHJ9EHWnhAq

```

Take note of your secret seed and your public key, they're gonna be required in the next step.

#### Add your sessions keys to Aura

Assuming that your node is running and accessible through DNS, connect to it via PolkadotJS Apps.

1. Go to [`https://polkadot.js.org/apps/?rpc=wss://your-node-address#/rpc`](https://polkadot.js.org/apps/?rpc=wss://rpc.pendulumchain.tech)``
2. Select the RPC method: `author` -> `insertKey(keyType, suri, publicKey)` &#x20;
3. Complete the fields:
   1. keyType: **aura**
   2. suri: your secret phrase or secret seed (both are accepted)
   3. publicKey: your public key either in SS58 format or hexadecimal.

As an example, with the above generated keys it would look like this:&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot from 2022-10-20 12-40-28.png" alt=""><figcaption><p>Insert Aura session keys for collator node.</p></figcaption></figure>

Submit the RPC call, and you are good to go now!
