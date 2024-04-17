---
description: Move tokens from the testchain to Stellar
---

# Redeem assets

## With the _Portal_

Navigate to the bridge tab on the portal and click on "Back To Stellar" on the widget:

* Select the asset and the amount you want to redeem
* Enter your wallet address

![](<../../../../.gitbook/assets/image (3) (1).png>)

From there, it might take up to 48h for the vault to transfer the funds back

### Status of the Transaction

You can verify the status of your bridge requests anytime under the transfer page. You can also see the details if you need more information about the transaction.

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## With Polkadot.js

Similarly to an issue request, using the polkadot.js portal requires further knowledge:

* Head to the _Extrinsics_ tab
* Select the _redeem -> requestRedeem_ extrinsic
* Fill in the values:
  * **amountWrapped** - the amount you want to bridge back to Stellar
  * **stellarAddress** - the address of the account that you want to receive the tokens on
  * **vaultId::accountId -** the account ID of the vault's Substrate account
  * **vaultId::currencies::collateral -** the token that the vault uses as collateral
  * **vaultId::currencies::wrapped -** the token that will be bridged
    * With the `vaultId` fields you are basically selecting the vault you want to use for bridging. In order for this to work, a vault with these values has to be registered on-chain.&#x20;

<figure><img src="../../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
