# Recovering a vault after liquidation

If a vault you operate gets liquidated, the collateral is confiscated. To make the vault operational again, you have to deposit new collateral and register it again. When a vault is liquidated, Spacewalk considers the locked tokens on Stellar to be lost. This means you can use the tokens that users locked in the vault’s Stellar account to retrieve new collateral. For this, you can either

1. Trade the tokens for the collateral asset on a CEX, or
2. If other vaults for the same wrapped asset are available, bridge the tokens available on the vault’s Stellar account to Pendulum using the other vaults and perform liquidation redeems against the liquidation vault to get back parts of the confiscated collateral.

In order to change the vault’s status from `Liquidated` back to `Active` you need to call the `vaultRegistry::recoverVaultId()` extrinsic. A prerequisite for this is that the vault does not have any pending issue or redeem requests. Otherwise, it first needs to fulfill those before it can be ‘recovered’. You can check for pending bridge requests with the `vaultRegistry::vaults()` storage query. The field `toBeRedeemedTokens` needs to be at `0`.

<figure><img src="../../../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

If the `vaultRegistry::recoverVaultId()` extrinsic executes successfully, the `status` of your vault should change back to `Active: true` meaning that it’s active and willing to accept issue requests again.

Afterward, you can deposit new collateral as usual by calling the `vaultRegistry::depositCollateral()` extrinsic.
