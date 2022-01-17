# Connect Account

The first time you access the Prototype, you will see the screen below, meaning that no account is connected yet.

To connect an account, there are two options:

1. Connect an existing Stellar account
2. Create an account with some testnet tokens in **one click**.

## Option 1: Connect an existing Stellar Account

![](../../.gitbook/assets/image.png)

If you click on the “CONNECT ACCOUNT” button, a dialog pops up.

![](<../../.gitbook/assets/image (16).png>)

You need to provide a name for the account, and your **stellar secret key** (a string that starts with an "S")**.** After that, clicking on “Connect account” will save this key in the local storage and connect to the Pendulum address of that account.

You can reveal your password to copy it for later use via the icon on the right side of the secret key input.

After connecting, the balances page will be updated, reflecting your balances on Pendulum.

![](<../../.gitbook/assets/image (17).png>)

## Option 2: One-click account setup

The other way you can connect your account is meant for users that do not have a Stellar testnet account, and especially those who do not have our testnet EUR or USDC tokens to play around with the provided AMM. For this wide use case, a special feature was developed called **One-click setup**. To use it open the account dialog by clicking on “Connect Account” and then on the button “One-click setup”. This will start a sequence of events:

* You will have one Stellar account created
* Another one for the Pendulum network, whose address will be derived from the stellar account.
* You will receive XLM tokens courtesy of the Stellar _friendbot_.
* You will have _trustlines_ created for our testnet tokens: EUR and USDC.
* Furthermore, your Stellar account will be funded with some of our testnet EUR and USDC.
* On the Pendulum side, you will get some native PEN tokens to be able to use the different services of the network, courtesy of the Pendulum faucet.

![](<../../.gitbook/assets/image (9).png>)

After the creation the Stellar key is shown, so you can actually copy it right away and add it to your Stellar wallet of preference (we recommend [Solar](https://solarwallet.io)).

![](<../../.gitbook/assets/image (7).png>)

You will notice that your PEN balance is increased by 10000 but, you still don’t have any EUR or USDC tokens _**on the Pendulum side.**_

![](<../../.gitbook/assets/image (10).png>)
