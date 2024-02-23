---
description: >-
  Spacewalk distributes fees generated from issue and redeem operations to
  collateral providers and nominators. These fees are paid in the wrapped
  currency associated with the operation.
---

# Vault rewards

### Approach

* Fixed PEN / block / month, decreasing each month
* Reward is defined for each collateral based on the USD value in the pool (distributed proportionally)
* Total amount = 12,000,000 AMPE tokens distributed for 24 months dynamically based on a decay rate of 3.75674) - 6% of the token allocation reserved for Vault rewards
* Initial month's allocation: 750,000 AMPE i.e. 750,000/(number of blocks in a month), followed by a decay rate of 3.75674% for each subsequent month until 24 months
* Distribution of the reward proportional to the fraction of the stake of a vault (assets are first converted to USD and based the their USD value of stake the rewards are distributed)

## Implementation

### Pool types <a href="#d01b" id="d01b"></a>

This implementation uses the following types of pools. We distinguish between pools that are used to store pending rewards to be paid out vs. pools that are used to hold collateral. These two pool types correspond to the two-layer system explained above, namely, Nominator Stake Tracking and Distribution Pools for managing pending rewards distribution, and Collateral Currency Pools for handling and securing the collateralized assets

* (**Reward**) _Each_ **collateral** **currency** used in Spacewalk has its own pool for storing rewards. We will call it `CollateralRewardPool(currency)`.
* These are configured to have `PoolId = CurrencyId` and `StakeId = VaultId`, meaning that the pools are identified by a `CurrencyId` (the collateral currency) and the stakes are deposited by `VaultId`s
* Managed by the `PooledRewards` pallet.
* (**Collateral**) _Each_ vault has its own internal **collateral** **staking pool** that is used by the nominators to contribute to the collateral and is used to distribute the slashing across all participants of that vault.
* This pool is used to **hold the **_**collateral**_ of each vault and it also keeps tracks of the rewards each nominator has pending on the vault, although this operation does not happen every time fees are distributed.
* Managed by the `Staking` pallet.

### Distributing the reward to each vault based on the collateral price <a href="#id-5db9" id="id-5db9"></a>

When distributing the reward, we need to consider not only the quantity of collateral provided, but also its current value. For instance, the price of 1 KSM is not equal to the price of 1 USDT, so providing collateral of 1000 KSM versus 1000 USDT should yield different rewards. To accommodate for this, we:

* Calculate the USD value of the total collateral deposited across all collateral currencies
* For each collateral currency:
* Calculate the value of the stake in USD
* Calculate the percentage of how much this collateral contributes to the total collateral.
* Multiply this percentage times the total reward to derive the ‘fair share’ and deposit this reward into the _CollateralRewardPool_ of that collateral currency

