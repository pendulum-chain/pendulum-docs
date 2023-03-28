# Delegation

## How to delegate

In order to stake with a collator, you must first find a collator.

To look up a list of available collators:

1. Navigate to the tab `Developer` > `Chainstate`&#x20;
2. Query for: `parachainStaking` and select the `topCandidates()` function
   1. You can see all collators by selecting the `candidatePool()` option and toggling options **off**
3. You can now select an ID to delegate to

<figure><img src="../../.gitbook/assets/Screenshot_2022-11-16_at_15.22.22.png" alt=""><figcaption><p>Select an owner-id as a collator to delegate to</p></figcaption></figure>

```bash
Do note that due to the current UI implementation on Polkadot.js staking X 
amount requires the addition of 12 0s 
Staking 10 → 10 000 000 000 000
```

You can correctly delegate by filling the previous form with one or more of these `ids`

The transaction can now be submitted to perform the join delegators action

## Delegating - Join delegators action

In order to join a delegator a user has to:

1. select the `parachainStaking` extrinsic
2. select the `joinDelegators` action
3. Lookup a collator address in order to find them

<figure><img src="../../.gitbook/assets/Screenshot_2022-11-16_at_15.37.23.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You can verify the amount you have staked on your accounts tab
{% endhint %}

<figure><img src="../../.gitbook/assets/image (3) (3).png" alt=""><figcaption></figcaption></figure>
