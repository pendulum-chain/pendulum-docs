# Asset Redemption Post-Vault Liquidation

When an undercollateralized vault is liquidated:

1. The Vaults entire collateral is slashed
2. The bridge initiates a first-come-first-served liquidation swap:

Holders of assets on Amplitude and Pendulum can now use the `redeem.liquidationRedeem()` extrinsic to burn their assets and receive a portion of the confiscated collateral in return. This process involves exchanging the asset originally associated with the liquidated vault for a share of the confiscated assets provided by the vault. However, if the price of the collateral asset continues to decrease after the vault’s liquidation, the actual premium received by users may vary and could be lower than initially anticipated due to market fluctuations.

Steps to Redeem Assets During Vault Liquidation:

1. **Navigate to the Extrinsic Submission Page on polkadot.js** Go to the section where you can submit extrinsics.

* **Select the `redeem.liquidationRedeem()` Extrinsic:**

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-07-29 at 15.31.47.png" alt=""><figcaption></figcaption></figure>

2. Choose Collateral asset ID
3. Wrapped asset = asset to be redeemed
4. Amount wrapped = amount to be redeemed

You will need to specify the amount of assets you wish to redeem.

Please note all our assets have different decimals. You can check in our asset registry as explained below.

5. Submit transaction to receive the collateral asset.

**You can use the encoded call data below and modify it as needed:**

Instead of manually following each step to redeem assets during a vault liquidation, you can also use the below encoded call data to streamline the process. Simply modify the encoded call data as needed and submit it directly through the extrinsic submission page on polkadot.js.

Encoded code data 0x410101000200070010a5d4e8

* **Account:** Update with your account address.
* **Amount:** Specify the amount of the asset you wish to burn.
* **Redeem Asset:** Indicate the asset being burned.
* **Collateral Asset:** Specify the asset you will receive in return.

To find the Asset Decimals, Redeem Asset ID and Collateral Asset ID, follow these steps:

1. **Access Polkadot.js:**
   * Navigate to Polkadot.js for either Pendulum or Amplitude.
2. **Go to the Developer Section:**
   * Select the "Developer" tab in the top menu.
3. **Open Chain State:**
   * Click on "Chain State" to access state queries.
4. **Select the State Query:**
   * Choose "assetRegistry" from the state query options.
   * Set the selection to "metadata."
5. **Locate Asset IDs:**
   * The results will display all assets registered on the network along with their respective IDs.
   * Refer to the sample data provided below to find the specific Asset ID you need.

KSM, Asset ID = XCM:0

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-08-09 at 08.55.24.png" alt=""><figcaption></figcaption></figure>

**User Benefit:**

Liquidation is designed with user security and value maximization in mind. By participating in the liquidation swap, users can take advantage of a premium exchange rate, thereby receiving a higher value in KSM compared to typical market rates. This ensures that even in the event of liquidation, users can benefit from favorable terms.

