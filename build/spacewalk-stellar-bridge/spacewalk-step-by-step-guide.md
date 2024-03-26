---
description: >-
  This guide will walk you through the process of bridging Spacewalk assets to
  Pendulum and back to Stellar.
---

# Spacewalk Step-by-step guide



{% hint style="info" %}
This guide focuses primarily on the Lobstr wallet because of its comprehensive features and user-friendly interface. However, you are free to use any Stellar wallet of your choice.
{% endhint %}

**Bridging to Pendulum**

## **Step 1: Stellar Wallet Setup**

Begin by creating a Stellar wallet. Visit [Lobstr](https://lobstr.co/authorization/signin/?next=/home/) wallet and follow the prompts to set up your account. If you already have a Lobstr wallet with Stellar assets then proceed to step 4.

![](https://lh7-us.googleusercontent.com/9i\_1kbqw-EC1h5FeKmQhFlTD\_Sjcrjfyx2-68H7erImy7d46P-DJ9-nQN98La7\_SVCFVtHbO3eb3Pdq8JYVrLHj2HxSIppZY5Dn8G88xSizGfNCnkOXsVUF-VIfWPQCwhOd8l3JRuJgZNwzn9owGjAY)

## **Step 2: Acquire Assets on Lobstr**

On Lobstr, purchase assets such as EURC, BRL, XLM, NGNC, AUDD or TZS.

Utilize [MoonPay or Stripe](https://lobstr.co/buy/) for transactions, available through Lobstr's partnerships.

![](https://lh7-us.googleusercontent.com/TXz2VWWqesKINLAsTVfyUSIARJu4lMAhd0rQ9v\_L8XxuTT0Bud8RPi6S3bXa-EjHVYNl3SAIjj8f2dAWo6A5Yy18KXwE002LlIfFGUupfXLQkClI4bsLCJMjLeXyNSIZMR4uHfiDn0hXnSwoL1CSRog)

## **Step 3: Exchange for Stellar Stablecoins**

Once you have USDC or XLM you can go to Step 4 and bridge to pendulum. If you want to bridge other stablecoins like BRL, TZS etc then you can use Lobstr's [Stellar swap feature](https://lobstr.co/swap) to exchange XLM or USDC for the stablecoin of your choice that you wish to bridge to Pendulum.

![](https://lh7-us.googleusercontent.com/4S6ISReR63ZxgM56JJ4eLboD9MCwJ0PAIpyohGN5w7O82G3HayUP-gmnpPK7eljbL7Fi0nZWAFbDATxPyaiuUMRbkIaJAczBCXcPBCU8wFpXKCdVJnZcyLVGYy8nZFQze-Sr9c0uQp17kyczx5foKAI)

Alternatively, you can place a sell order on Stellar's Orderbook DEX, opting for either a limit or market order. Proceed to the next step once you have acquired your desired stablecoin. Both methods have minimal fees.

## **Step 4: Get a Polkadot Wallet**

If you already have a Polkadot wallet skip to step 5. For a user-friendly wallet experience we recommend [Talisman](https://www.talisman.xyz/) or [Subwallet](https://www.subwallet.app/). Learn more about choosing the right [Polkadot wallet for your needs here](https://medium.com/pendulum-chain/securing-your-pen-ampe-tokens-choosing-the-right-wallet-d754334351bb).

## **Step 5: Get PEN**

You will need PEN to fund the gas fees for Spacewalk transactions. If you already have PEN jump to step 6. If you don’t have PEN yet you can acquire from a CEX or DEX:

**From centralized exchange (MEXC)**\
Signup with [MEXC](https://www.mexc.com/exchange/PENDULUM\_USDT) and purchase Pendulum ([step-by-step guide](https://medium.com/pendulum-chain/step-by-step-guide-how-to-trade-pendulums-pen-token-on-mexc-c47a5444e712)). Withdraw your PEN tokens to your Pendulum address. If you need help setting up your Polkadot/Pendulum wallet, check out our [docs](https://pendulum.gitbook.io/pendulum-docs/community/pen-and-ampe-wallets).

**From decentralized exchanges (DEX)**\
You can swap a variety of Polkadot native assets (e.g. DOT, USDT, USDC) for PEN tokens using the [Stellaswap trading UI](https://app.stellaswap.com/exchange/swap) on Moonbeam. To bring your Polkadot assets to Moonbeam, you can use the [Cross-chain transfer UI](https://app.stellaswap.com/bridge/xctransfer) from Stellaswap.

## **Step 6: Bridge the Asset Using Spacewalk**

Navigate to the Pendulum Spacewalk bridge [here](https://portal.pendulumchain.org/pendulum/spacewalk/bridge). Choose 'To Pendulum' and select the asset you wish to bridge. Enter the token amount and click 'Bridge.' If you have not yet connected your Polkadot wallet (e.g., Talisman, Subwallet, Polkadot.js) you'll be prompted to do so, and then click ‘Approve’.

![](https://lh7-us.googleusercontent.com/2sHD3PfdBLlsDuE03eTQoQ9n9I61BMlgerNmCgIJUxRl\_dMN-2fXtbhpIklq2Kwc2QXFOaJZ0JkibE-aaj2Rt5KjW90jI-2cymYiZIM-PZ6oPPCzNbPPx7gZOzmmRBUveOFYnk2KDsCbaQx1R3K9WgM)



{% hint style="info" %}
If the network is busy it may take a few seconds to process after clicking Bridge, please wait.
{% endhint %}

<img src="https://lh7-us.googleusercontent.com/uWY2hDFt9NEM2BPu6kwyX04Idhavu2qFmkfxUrcVNgBxgJH7HbGLgNfnxa14fdL_EWq4OnD7_jSsqPE5JXBAmMG5FjnbwW7GHIxIlk_veQrVSN3o1D-qb3J3iIP80Ms5q5_bH18NqXptm0fJaiP4ORs" alt="" data-size="original">

## **Step 7: Deposit via Lobstr**&#x20;

Return to Lobstr and select 'Send' from the left-hand tabs. Enter the deposit details as provided by the Spacewalk bridge. Ensure to paste the recipient's address from the 'In a single transaction to' section. Tick the 'Add Memo' box to input the required text memo. Note: if you do not include the memo you coins will be lost. Stellar transactions require memos. Review your payment details before clicking 'Send.'

![](https://lh7-us.googleusercontent.com/nIa2IhfMfB2mxGRmc3RHJoKD0Px8B020Azkl--0iNM3m6wZHOFYLpZN7N9LyO5YtUXu\_O4vDH3wDy3zJ\_Jb9fo3CIK6dC4bDXXGACpl6ttBDrWTvGTIH7nlI-EtXCyF4dU5TyhvL6L52Jn6CaTdSA-U)

Then review the payment details and click ‘Send’.

![](https://lh7-us.googleusercontent.com/aCSqwGhrN7NYz0CxJD\_2zL91vcXy3zOiW\_FsMyUPd1xt-hSBCszVjlYBEms6olQgymc4TGivKpmM3T3N6IR5\_TQQuKpKBy\_2AYynjYLoI5WlGmtAhT4WN7KyXq85LTSd3KgiQq3qgBkOvAPYmeJuK4U)

Once Lobstr confirms the payment, go back to the Spacewalk Bridge interface and confirm the transaction by clicking 'I have made the payment.'

## **Step 8: You have successfully Spacewalked!**

The bridging transaction typically completes within a minute. Monitor the transaction status via the ['Transfers'](https://portal.pendulumchain.org/pendulum/spacewalk/transfers) tab on the Spacewalk bridge UI. The UI will indicate ‘Pending’ until the transfer is ‘Completed’. If your transaction hasn't been processed after 10 minutes, contact support through [Telegram](https://t.me/pendulum\_community) or [Discord](https://discord.gg/KJybDMtfXt) for assistance.

<figure><img src="https://lh7-us.googleusercontent.com/0cGNvTAp0mjJ0LiPoLk6uTDHotRdrH7s_ZRQS-B2O1NLvbvaVjKxwcY63XnJaubu6X0hp0OtIw-uSiJvtliY2xRWMusQ8EbHDvPbvGe1f48wpLoyJK5kBOS-XPH6rMSWYxJ-5ukuBJ3Z9-lIC8QYHVE" alt=""><figcaption></figcaption></figure>

**Bridging from Polkadot to Stellar**\
The same process in reverse can be used for bridging assets back to Stellar. First click ‘Back to Stellar’ on [Spacewalk Bridge](https://portal.pendulumchain.org/pendulum/spacewalk/bridge), select the asset you wish to bridge back and the amount of tokens. Copy and paste your Lobstr wallet address (or any Stellar wallet address) and then click ‘Bridge’ and approve in your Polkadot wallet.&#x20;

![](https://lh7-us.googleusercontent.com/cPFE1XJghGxbGyplxTAgxQHV3pjJkfWosZ1-mTQeMqV23nC2DBQPsb4FZ9HOgQaRcJD-CT0a1ZfMy\_8KMVcULFlHkpYMXSB3ZXpwPImVF3uOchKBlG3oKalcPt4v8CI5gfNKHwxylKDzAy2JxnCpbMo)

![](https://lh7-us.googleusercontent.com/TQQ7m7gWRunOqKfxnQDJthKAsvS6-YNBCS\_SLDhYv5dN8OKbBf4QpwN7HO8Hor6ZbbZj1186toz43qELveQI5Q0A5WuAOpU-eTnttGBkorSoeUQAYvCoAL4doWpwONKj0CpMhNrTErsEN6Pvij2IH64)

\
