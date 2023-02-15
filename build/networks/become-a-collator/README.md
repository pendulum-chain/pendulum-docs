# Set up Collator

This guide will describe how to install and run an Amplitude Collator node on docker. The following link will contain the location of the Docker images:

[https://hub.docker.com/repository/docker/pendulumchain/pendulum-collator](https://hub.docker.com/repository/docker/pendulumchain/pendulum-collator)

### Hardware and Software requirements

In order to be able to run a collator node, you will need at least a machine with the following specs:

* 4 CPU cores
* 16 GB of RAM
* 250 GB of Disk space
* Ubuntu 20.04.5 LTS

:warning: Even though other Ubuntu and Debian versions may work, they were not tested, and we only provide support for the Ubuntu version mentioned above.

### Step-by-step installation

We assume that your Ubuntu server is a fresh install, it does have an external IP address that has direct access to the internet.

Apply the latest patches

```bash
sudo apt update
sudo apt upgrade -y
```

Follow the steps below to install docker on your Ubuntu server:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common git binutils -y
curl -fsSL <https://download.docker.com/linux/ubuntu/gpg> | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] <https://download.docker.com/linux/ubuntu> `lsb_release -cs` stable"
sudo apt update
sudo apt-cache policy docker-ce 
sudo apt install docker-ce -y
sudo systemctl status docker
sudo groupadd docker
sudo usermod -aG docker $USER
su -s ${USER}
```

Configure your local firewall to allow communication for the required ports

```bash
sudo ufw allow 8844/tcp
sudo ufw allow 30335/tcp
sudo ufw allow 9955/tcp
sudo ufw allow 30334/tcp
sudo ufw allow https
sudo ufw enable
```

Download chain specifications

```bash
sudo mkdir -p /data/
sudo wget -P /data <https://raw.githubusercontent.com/paritytech/polkadot/master/node/service/chain-specs/kusama.json>
sudo wget -P /data <https://raw.githubusercontent.com/pendulum-chain/pendulum/main/res/amplitude-spec-raw.json>
```

Install the application using docker. This will name the docker container the same as the hostname of the Ubuntu server. If you wish to change that, replace the **$(hostname)** parameter with a name of your choice.

```bash
sudo docker pull pendulumchain/pendulum-collator:v0.9.24
docker run --name $(hostname) --restart unless-stopped -d -v /data:/data -it -p 30335:30335 -p 9955:9955 -p 30334:30334 -p 8844:8844 pendulumchain/pendulum-collator:v0.9.24 --collator --allow-private-ipv4 --unsafe-ws-external --rpc-cors all --rpc-external --rpc-methods Unsafe --force-authoring --enable-offchain-indexing=TRUE --ws-port 8844 --ws-max-connections 200 --port 30335 --rpc-port 9955 --chain /data/amplitude-spec-raw.json --execution=wasm -- --port 30334 --chain /data/kusama.json --database=RocksDb --execution=wasm -d /data --unsafe-pruning --pruning=256
```

### Verify your installation

Run **`docker ps`** command to verify if the collator is running properly. You should see the following output:

```bash
# docker ps
CONTAINER ID   IMAGE                                     COMMAND                  CREATED          STATUS          PORTS                                                                                                                                                                   NAMES
3212d72e1291   pendulumchain/pendulum-collator:v0.9.24   "tini -- /usr/local/…"   10 minutes ago   Up 10 minutes   0.0.0.0:8844->8844/tcp, :::8844->8844/tcp, 0.0.0.0:9935->9935/tcp, :::9935->9935/tcp, 0.0.0.0:30334-30335->30334-30335/tcp, :::30334-30335->30334-30335/tcp, 9945/tcp   yourhostname
```

The **/data** directory should start to get populated with data and should have a structure:

```bash
drwxr-xr-x 3 root root    6144 Sep 28 11:09 chains
-rw-r--r-- 1 root root 2861651 Oct  4 16:36 kusama.json
-rw-r--r-- 1 root root 1326607 Oct  4 16:36 amplitude-spec-raw.json
```

### What happens next?

Now your collator will start syncing both **Kusama** and **Amplitude** chains. Kusama syncing may take several days to complete due to the size of the Kusama database, this is normal and expected. You can follow the progress in the log files using the **docker logs -f $(hostname)** command.

```bash
2022-09-28 19:02:26 assembling new collators for new session 45 at #52800
2022-09-28 19:02:30 ✨ Imported #14652094 (0x7505…a7d8)
2022-09-28 19:02:30 💤 Idle (49 peers), best: #14652094 (0x7505…a7d8), finalized #14652090 (0xbc43…9e95), ⬇ 488.0kiB/s ⬆ 425.0kiB/s
2022-09-28 19:02:31 ⚙️  Syncing 224.8 bps, target=#181974 (12 peers), best: #53857 (0x2f61…0009), finalized #0 (0xccea…1aaf), ⬇ 1.4MiB/s ⬆ 2.1kiB/s
```

When the node is syncing, you can see the block it is trying to sync up to. The “**best**” section will tell you what block the sync actually is at, and the “**target**” where it needs to get to.

#### How to speed up the Kusama chain syncing process?

As we previously pointed out, syncing the **Kusama** chain could take many days. Luckily enough, there is a solution for that provided by [Polkashots](https://polkashots.io/). Follow the procedure here:[https://ksm-rocksdb.polkashots.io/](https://ksm-rocksdb.polkashots.io/) to try and speed up your sync procedure.

💡 Polkashots is a 3rd party service provider and in no way affiliated with Pendulum/Amplitude

### Insert your Aura keys

While waiting for the node to finish syncing, you can already proceed with the next required step. This is about inserting an authority key pair to your node, i.e. a pair of private and public keys that will allow you to have control on the node, and it's required for the next step, where we will guide you through the staking and rewards configuration.

So, if you already own an account that you want to use, you can skip the next section. But if you still don't have a key pair already generated, let's first do that.

#### Generating Aura keys

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

### Staking and becoming a collator

Your node is now ready to collate but will not yet be selected for collating. Our pallet parachain-staking will select collator candidate nodes to become actually collating nodes on a regular basis. In order to be selected, your node first needs to stake some amount of native AMPE tokens with this pallet. The minimum staking amount is 5000 AMPE tokens. Follow these steps:

1. Go to [polkadot.js](https://polkadot.js.org/apps) and select Amplitude from the _Kusama & Parachains_ folder
2. Go to Accounts -> Accounts and add the account belonging to your Aura key assigned to your collator node in the previous step: click "+ Add Account", enter the secret phrase or secret seed of your Aura session key and enter a password and a name.
3. Go to Developer -> Extrinsics and choose the account for your Aura key. Select the extrinsic **parachainStaking** -> **joinCandidates** and select a staking amount. The staking amount is the amount of AMPE tokens times 1 trillion (an additional 12 zeros). The minimum staking amount is 5000 AMPE tokens, so that the minimum value to enter is 5,000,000,000,000,000.
4. Submit the transaction.
5. Go to Developer -> Chain state and select parachainStaking -> topCandidates. Press the "+" button and check that your aura key occurs in the list of top candidates. If it does not, then you would need to increase your staking amount in order to become a top candidate. Whether your collator is a top candidate depends on your staking amount and on the total staking amount of your delegators. In order to increase your staking amount, proceed as in step 3 but choose the extrinsic **candidateStakeMore**.

<figure><img src="../../../.gitbook/assets/Screen Shot 2022-10-20 at 14.06.01.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Please, be aware that after you stake, your collator will be part of the collator set, meaning it is selectable by the algorithm to produce blocks :ok\_hand:

**But If your collator is not running properly, this will impact negatively the blocktime of the network**, so it's important to double check that after the collator finished syncing, it is healthy and producing blocks.
{% endhint %}

