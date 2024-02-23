---
description: >-
  Claiming rewards involves using the rewardDistribution.collectReward extrinsic
  with specific parameters.
---

# Claiming Vault rewards

### How to claim rewards for Spacewalk on Amplitude?

1. Go to [https://polkadot.js.org/apps/](https://polkadot.js.org/apps/) and switch to **Amplitude** network from the network menu or directly click on this [link](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc-amplitude.pendulumchain.tech#/extrinsics/decode).
2. Find `Developer` in the top menu, and choose `Extrinsics` from the drop down. Select the `Decode` tab

<figure><img src="../../../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Top tab</p></figcaption></figure>

3. For USDC, BRL, TZS paste the below in the field `hex-encoded call`&#x20;

`0x4901d0925b8a6233c50f35eab7236336b4a90a4ec0435bb45d0e525918a62fbb403401000201555344433b9911380efe988ba0a8900eb1cfe44f366f7dbe946bed077240f7f624df15c50000`

For XLM Paste the below in the field `hex-encoded call`

`0x4901663126f066aec3cc5d827e9513fae957dced9695cb1db17696098798689f282501000200020000`



<figure><img src="../../../../.gitbook/assets/Screenshot 2024-02-16 at 14.46.11 (1).png" alt=""><figcaption></figcaption></figure>

4. Now switch to the `Submission` tab
5. Make sure the **'using the selected account'** and '**accountId'** fields are filled with your Vaultid

{% hint style="info" %}
`vaultId` is  the account id of the vault, however it also contains information of what collateral the vault uses and what wrapped assets it supports to be bridged. That way the same vault account can deploy multiple vaults for different swap assets – each of them would then have a different vault id.
{% endhint %}

6. Stellar: SpacewalkPrimitivesAsset choose AlphaNum4

{% hint style="info" %}
AlphaNum4 - asset has 4 or less characters, AlphaNum 12 - asset has 12 or less characters
{% endhint %}

7. Provide AlphaNum4: {code: \[u8;4], issuer: \[u8;32]}, which is the currency code as per below:

* USDC - USDC
* BRL - `0x42524c00`
* TZS - `0x545a5300`
* NGNC - NGNC
* EURC - EURC
* AUDD - AUDD
* XLM - Stellar: SpacewalkPrimitivesAsset is StellarNative

8. Choose the Issuer

{% hint style="info" %}
Issuer is public key of the Stellar issuer address issuing a particular currency
{% endhint %}

Issuer:

*   USDC:&#x20;

    0x3b9911380efe988ba0a8900eb1cfe44f366f7dbe946bed077240f7f624df15c5
* BRL: `0xeaac68d4d0e37b4c24c2536916e830735f032d0d6b2a1c8fca3bc5a25e083e3a`
* TZS: `0x34c94b2a4ba9e8b57b22547dcbb30f443c4cb02da3829a89aa1bd4780e4466ba`
* AUDD: 0xc5fbe9979e240552860221f4fe2f2219f35e40458b8b58fc32da520a154a561d
* EURC: 0x2112ee863867e4e219fe254c0918b00bc9ea400775bfc3ab4430971ce505877c
* NGNC: 0x241afadf31883f79972545fc64f3b5b0c95704c6fb4917474e42b0057841606b
* XLM: not required

9. Make sure `rewardCurrencyId`: `SpacewalkPrimitivesCurrencyId` is Native
10. Submit transaction

{% hint style="info" %}
`Please note, there is no need to provide the issuer for` XLM asset
{% endhint %}

10. After successfully submitting the transaction, a confirmation prompt will appear in the upper right corner.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-02-20 at 12.01.27 (2).png" alt=""><figcaption></figcaption></figure>

11. You can check the polkadot.js explorer for details

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-02-20 at 12.05.50.png" alt=""><figcaption></figcaption></figure>

