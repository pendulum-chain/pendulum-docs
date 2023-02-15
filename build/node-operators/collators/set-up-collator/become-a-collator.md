# Become a Collator

###

### Staking and becoming a collator

Your node is now ready to collate but will not yet be selected for collating. Our pallet parachain-staking will select collator candidate nodes to become actually collating nodes on a regular basis. In order to be selected, your node first needs to stake some amount of native AMPE tokens with this pallet. The minimum staking amount is 5000 AMPE tokens. Follow these steps:

1. Go to [polkadot.js](https://polkadot.js.org/apps) and select Amplitude from the _Kusama & Parachains_ folder
2. Go to Accounts -> Accounts and add the account belonging to your Aura key assigned to your collator node in the previous step: click "+ Add Account", enter the secret phrase or secret seed of your Aura session key and enter a password and a name.
3. Go to Developer -> Extrinsics and choose the account for your Aura key. Select the extrinsic **parachainStaking** -> **joinCandidates** and select a staking amount. The staking amount is the amount of AMPE tokens times 1 trillion (an additional 12 zeros). The minimum staking amount is 5000 AMPE tokens, so that the minimum value to enter is 5,000,000,000,000,000.
4. Submit the transaction.
5. Go to Developer -> Chain state and select parachainStaking -> topCandidates. Press the "+" button and check that your aura key occurs in the list of top candidates. If it does not, then you would need to increase your staking amount in order to become a top candidate. Whether your collator is a top candidate depends on your staking amount and on the total staking amount of your delegators. In order to increase your staking amount, proceed as in step 3 but choose the extrinsic **candidateStakeMore**.

<figure><img src="../../../../.gitbook/assets/Screen Shot 2022-10-20 at 14.06.01.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Please, be aware that after you stake, your collator will be part of the collator set, meaning it is selectable by the algorithm to produce blocks :ok\_hand:

**But If your collator is not running properly, this will impact negatively the blocktime of the network**, so it's important to double check that after the collator finished syncing, it is healthy and producing blocks.
{% endhint %}
