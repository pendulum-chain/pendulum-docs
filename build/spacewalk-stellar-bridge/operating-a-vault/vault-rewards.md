---
description: >-
  Spacewalk distributes fees generated from issue and redeem operations to
  collateral providers and nominators. These fees are paid in the wrapped
  currency associated with the operation.
---

# Vault rewards



### Assumptions

* 6% of the token allocation reserved for Vault rewards
* Reward is defined for each collateral based on the USD value in the pool (distributed proportionally)
* Total income for vaults is in fees (wrapped tokens) + AMPE rewards. Since issue and redeem fee is initially zero, the reward pot will only contain minted tokens.
* Capacity is defined as the allowed issuance based on the collateral provided (Collateral amount / Secure collateralisation factor 160%)



### Approach

* Fixed PEN / block / month, decreasing each month
* Total amount = 12,000,000 AMPE tokens distributed for 24 months dynamically based on a decay rate of 3.75674) - 6% of the token allocation reserved for Vault rewards
* Initial month's allocation: 750,000 AMPE i.e. 750,000/(number of blocks in a month), followed by a decay rate of 3.75674% for each subsequent month until 24 months
* Distribution of the reward proportional to the fraction of the stake of a vault (assets are first converted to USD and based the their USD value of stake the rewards are distributed)
