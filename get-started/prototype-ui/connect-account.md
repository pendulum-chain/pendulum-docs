# Connect Account

The first time you access the Prototype, you will see the screen below, meaning that no account is connected yet.

To connect an account, there are two options:

1. Connect an existing Stellar account
2. Create an account with some testnet tokens in **one click**.

## Option 1: Connect an existing Stellar Account

If you click on the “CONNECT ACCOUNT” button, a dialog pops up.

![When not connected, an overlay is shown. Click on connect account to start using the webapp.](<../../.gitbook/assets/Screenshot from 2022-06-16 12-49-51.png>)

![Provide an account, or create one with the One Click Setup.](<../../.gitbook/assets/Screenshot from 2022-06-16 12-49-58.png>)

You need to provide a name for the account, and your **stellar secret key** (a string that starts with an "S")**.** After that, clicking on “Connect account” will save this key in the local storage and connect to the Pendulum address of that account.

You can reveal your password to copy it for later use via the icon on the right side of the secret key input.

After connecting, the Dashboard page will be updated, reflecting your balances on Pendulum.

{% hint style="success" %}
The Dashboard is the landing page of the prototype. Here you'll be able to see your Portfolio with your assets and the value in USD dollars (calculated through an exchange rate). and the Swap widget will allow you to easily exchange your assets using our provided AMM.
{% endhint %}

![](<../../.gitbook/assets/Screenshot from 2022-06-16 12-51-02.png>)

## Option 2: One-click account setup

The other way you can connect your account is meant for users that do not have a Stellar testnet account, and especially those who do not have our testnet EUR or USDC tokens to play around with the provided AMM. For this wide use case, a special feature was developed called **One-click setup**. To use it open the account dialog by clicking on “Connect Account” and then on the button “One-click setup”. This will start a sequence of events:

* You will have one Stellar account created
* Another one for the Pendulum network, whose address will be derived from the stellar account.
* You will receive XLM tokens courtesy of the Stellar _friendbot_.
* You will have _trustlines_ created for our testnet tokens: EUR and USDC.
* Furthermore, your Stellar account will be funded with some of our testnet EUR and USDC.
* On the Pendulum side, you will get some native PEN tokens to be able to use the different services of the network, courtesy of the Pendulum faucet.

After the creation the Stellar key is shown, so you can actually copy it right away and add it to your Stellar wallet of preference (we recommend [Solar](https://solarwallet.io/)).

![](<../../.gitbook/assets/Screenshot from 2022-06-16 13-01-33.png>)

You will notice that your PEN balance is increased by 10000 but, you still don’t have any EUR or USDC tokens _**on the Pendulum side.**_
