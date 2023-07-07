---
description: Moving tokens from Stellar to the testchain
---

# Issue assets

##

Issuing an Asset from the Portal App is straightforward:

* First, head to the Spacewalk - Bridge page
* In the displayed widget, make sure you're in the "**To Amplitude**" Tab
* Input the token, the amount, and if you want, the specific vault you want to use

<img src="../../../../.gitbook/assets/image (14).png" alt="" data-size="original">

{% hint style="info" %}
It might take a minute for the dialog to popup, do not navigate off the page!
{% endhint %}

After hitting bridge, a dialog will pop up asking you to make a transfer to the vault address with a specific message:

![](<../../../../.gitbook/assets/Screenshot 2023-05-24 at 12.28.37.png>)

Now, execute the transfer from your Stellar wallet of choice and confirm the payment.

### Status of Transaction

You can verify the status of your bridging requests anytime under the transfer page. You can also see the details if you require more information about the transaction.

<figure><img src="../../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

## With Polkadot.js

{% hint style="info" %}
Using the Polkadot.js portal is recommended only for expert users.
{% endhint %}

{% hint style="warning" %}
In order to know all the available assets you can bridge on Polkadot.js, run the following chain state query:\
vaultRegistry -> vaults()

This query will also display the required IDs for the extrinsics.
{% endhint %}

Usage of the polkadot.js portal requires knowing how to navigate the various extrinsics:

* Head to the _Extrinsics_ tab
* Select the _issue -> requestIssue_ extrinsic
* Fill in the values:
  * **amount** - of the token you want to bridge
  * **vaultId::accountId -** the account ID of the vault's Substrate account
  * **vaultId::currencies::collateral -** the token that the vault uses as collateral
  * **vaultId::currencies::wrapped -** the token that will be bridged
    * With the `vaultId` fields you are basically selecting the vault you want to use for bridging. In order for this to work, a vault with these values has to be registered on-chain.&#x20;

Just like with the portal, you will be required to execute a transaction after submitting the extrinsic. Finalize the transaction with the _executeIssue_ extrinsic.

<figure><img src="../../../../.gitbook/assets/image (3).png" alt=""><figcaption><p><strong>Note</strong> that for Stellar assets (besides XLM) you will have to specify them in the <em>Stellar::AlphaNum4</em> field.</p></figcaption></figure>
