# Rewards

## Claiming rewards

The respective method for checking a User’s rewards are under the ChainState tab

1. Navigate to the tab `Developer` > `Chainstate`
2. Query `parachainStaking` and select the `rewards()`action

<figure><img src="../../.gitbook/assets/Screenshot_2022-11-16_at_15.51.34.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Conversely to Chainstate operations, Extrinsics only report Success or failure at the top right of the screen:&#x20;

<img src="../../.gitbook/assets/Screenshot_2022-11-17_at_12.00.09.png" alt="" data-size="original">
{% endhint %}

Collator rewards can be claimed by:

1. Navigating to `Developer` > `Extrinsics` tab
2. Query `parachainStaking` and select the `incrementCollatorRewards()` action
3. Query `parachainStaking` and select the `claimRewards()` action

Delegator rewards can be claimed by:

1. Navigating to extrinsics tab
2. Query `parachainStaking` and select the `incrementDelegatorRewards()` action
3. Query `parachainStaking` and select the `claimRewards()` action



### Rewards Model

The **Reward Rate** is the constant rate at which staked tokens accrue rewards per individual block

The rewards rate for collators and delegators changes over time for both Parachains:

**Max Staking Rate** refers to the percentage of tokens of the **`total issuance`** (of the latest block) until the reward rate begins to decay.

The **Decay rate** is the velocity at which the reward rate for **collators** decreases annually, Collator's rewards decay every year by 6.17% (6.45% on Amplitude),&#x20;

In contrast, Delegator's rewards are reduced to 8%-7%-0% in the first two years (9%,8% and 0% for amplitude)



{% tabs %}
{% tab title="Pendulum" %}
<table><thead><tr><th width="167.66666666666666">Actor</th><th>Max Staking Rate</th><th>Reward</th><th>Decay Rate</th></tr></thead><tbody><tr><td>Collator</td><td>10%</td><td>11% </td><td>6.17% (of current reward)</td></tr><tr><td>Delegator</td><td>30%</td><td>8%</td><td>N/A</td></tr></tbody></table>
{% endtab %}

{% tab title="Amplitude" %}
<table><thead><tr><th width="167.66666666666666">Actor</th><th>Max Staking Rate</th><th>Reward</th><th>Decay Rate</th></tr></thead><tbody><tr><td>Collator</td><td>10%</td><td>11% </td><td>6.45% (Of current reward)</td></tr><tr><td>Delegator</td><td>40%</td><td>9%</td><td>N/A</td></tr></tbody></table>
{% endtab %}
{% endtabs %}
