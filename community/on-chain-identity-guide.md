---
description: How to set up on chain indentity on Pendulum?
---

# On chain identity guide

Here is the detailed [guide](https://support.polkadot.network/support/solutions/articles/65000181981-how-to-set-and-clear-an-identity) by Polkadot network on setting up an on-chain identity. This action requires a lock up of 10 PEN tokens, please ensure you have some additional tokens for gas fees.

Once you set the on-chain identity, below are the steps on how to verify it:

1. Go to Polkadot.js to find the accepted registrars of Pendulum: [https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc-pendulum.prd.pendulumchain.tech#/chainstate](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc-pendulum.prd.pendulumchain.tech#/chainstate)&#x20;
2. Select the 'identity' as query and then 'registars()' method and click on the '+' sign&#x20;
3. This should display the list of address's that are registars. Copy over the registars address and add it your address book.&#x20;
4. Now to verify your identity you need to request a judgement from a registar, go to Polkadot extrinsics: identity >> requestJudgement
   1. Two fields
5. regIndex - Index of registrar i.e 0 in our case, as there is currently only 1 registrar.&#x20;
6. maxFee - Add the fee you would like to pay to the registar, this can be anything. Make sure you add appropriate zeroes. 1 PEN = 1,000,000,000,000

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

6. Now you have to directly communicate with the registar you have requested the judgement from, this can done by clicking on the name of the registar and you will find his contact details

<figure><img src="../.gitbook/assets/Screenshot 2023-10-31 at 12.15.14 PM.png" alt="" width="278"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (25).png" alt="" width="375"><figcaption></figcaption></figure>

7. Once the registar confirms the request, your identity status would change from waiting to reasonable with a green check mark
