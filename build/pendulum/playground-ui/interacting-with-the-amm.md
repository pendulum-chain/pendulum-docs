# Interacting with the AMM

To interact with your deployed smart contract click on "All Contracts" in the sidebar and select your contract from the list of instantiated contracts.

![](<../../../.gitbook/assets/image (9).png>)

## Querying data

You can query metadata from the AMM. These include the total supply of minted LP tokens, the issuer and code of the pooled assets, the minimum liquidity of a liquidity pool, and the reserves/balances of the liquidity pool.&#x20;

![](<../../../.gitbook/assets/image (8).png>)

To do so, click on the "Message to Send" field and select one of the messages that don't specify arguments in the brackets. Since these calls only read data from the smart contract they can be sent as an RPC call so you don't have to create and sign a transaction for each query.&#x20;

## Deposit

To deposit assets to the liquidity pool select either `depositAsset1` or `depositAsset2` as the message to send. Enter the desired amount you want to deposit of your respective asset in the "amount" field shown beneath. You can only enter one amount because the corresponding amount that you have to deposit of the other asset is calculated automatically by the AMM.

{% hint style="info" %}
You receive so-called liquidity provider (LP) tokens for your deposit. These tokens are used to track your share of the pool and can later be used to withdraw your assets from the liquidity pool. LP tokens are unique for every liquidity pool.&#x20;
{% endhint %}

Click on "Call" to submit the transaction.&#x20;

## Swap

To swap assets with the AMM, select either `swapAsset1ForAsset2` or `swapAsset2ForAsset1` depending on which asset you want to swap for what. Specify how much of the other asset you want to receive in the "amountToReceive" field. The AMM internally calculates the amount you have to pay.&#x20;

Click on "Call" to submit the transaction.&#x20;

## Withdraw

To withdraw assets that you added to the liquidity pool, select the `withdraw` message and specify how many of your LP tokens you want to trade. The amount you receive of the pooled assets depends on your share in the liquidity pool.

You can query the current LP balance of accounts using the `lpBalanceOf` message.

Click on "Call" to submit the transaction.&#x20;

## Notes

You can tell the difference between a successful smart contract call and a failing one by looking at the number and types of events that are emitted after sending the transaction.

For example, as you can see here in the "Call Results" one of these calls has lots of events and a `system:ExtrinsicSuccess` so this was a successful call whereas the other one has fewer events and a `system:ExtrinsicFailed` among them.

![](<../../../.gitbook/assets/image (18).png>)

## &#x20;
