# Interacting with the AMM

To interact with your deployed smart contract navigate to the "[Execute](https://playground.pendulumchain.org/#/execute)" tab in the sidebar and click on the "Execute" button shown next to your contract in the list of instantiated contracts.

## Querying data

You can query metadata from the AMM. These include the total supply of minted LP tokens, the issuer and code of the pooled assets, the minimum liquidity of a liquidity pool, and the reserves/balances of the liquidity pool.&#x20;

To do so, click on the "Message to Send" field and select one of the messages that don't specify arguments in the brackets. Since these calls only read data from the smart contract they can be sent as an RPC call so you don't have to create and sign a transaction for each query.&#x20;

## Deposit

To deposit assets to the liquidity pool select either `deposit_asset_1` or `deposit_asset_2` as the message to send. Enter the desired amount you want to deposit of your respective asset in the "amount" field shown beneath. You can only enter one amount because the corresponding amount that you have to deposit of the other asset is calculated automatically by the AMM.

{% hint style="info" %}
You receive so-called liquidity provider (LP) tokens for your deposit. These tokens are used to track your share of the pool and can later be used to withdraw your assets from the liquidity pool. LP tokens are unique for every liquidity pool.&#x20;
{% endhint %}

Click on "Call" and "Sign & Submit" to submit the transaction.&#x20;

## Swap

To swap assets with the AMM, select either `swap_asset_1_for_asset_2` or `swap_asset_2_for_asset_1` depending on which asset you want to swap for what. Specify how much of the other asset you want to receive in the "amountToReceive" field. The AMM internally calculates the amount you have to pay.&#x20;

Click on "Call" and "Sign & Submit" to submit the transaction.&#x20;

## Withdraw

To withdraw assets that you added to the liquidity pool, select the `withdraw` message and specify how many of your LP tokens you want to trade. The amount you receive of the pooled assets depends on your share in the liquidity pool.

You can query the current LP balance of accounts using the `lp_balance_of` message.

Click on "Call" and "Sign & Submit" to submit the transaction.&#x20;

## &#x20;
