# Operating and Using a Vault

## Overview

A vault is an entity which provides bridging utilities to users. It achieves this, by provisioning the underlying infrastructure for bridging tokens. In a few words, it’s a safe,secure and trustless enabler

A user can safely bridge their assets through a vault in the Stellar chain, and receive an equivalent amount of wrapped tokens on the Pendulum network. In order for the vault to be able to provide their services, the vault locks up an amount of $DOT tokens. As an example, if they were to bridge $USDC, they’d receive a wrapped $USDC on the Pendulum network.



## Roles

### Vault User

A user will lock their stable-coins and bridge them across to Pendulum. In doing so, the user is given an equivalent amount of PEN tokens in order to use the features of the network.

{% hint style="info" %}
&#x20;At any point in time, the user can redeem their coins on the Stellar side
{% endhint %}

In doing so, the user gives up the custody of their stable-coins to a Vault, and incur the risk of having their valuable assets being stolen.

However, as The Vault is over-collateralized the Vault itself is not incentivized to steal coins. \
Vaults might choose to steal the stable-coins only in case of significant price drops and liquidity shortages.  In that case, users will be reimbursed **only with the asset the Vault has collateralized** - not the currency they initially started out with.

### Vault Operator

Vaults receive custody of assets from their users and inherently make a bet that the assets they collateralize will either stay constant or increase in value against stablecoin. Upon receiving custody of the assets they will release an equivalent amount of PEN tokens to allow users to operate.

Vaults have to release the locked tokens when users redeem their coins



### Oracle Agents - Relayers

{% hint style="info" %}
Do note that currently Oracle Agents are a part of the Vault client
{% endhint %}

Oracle agents are nodes that listen to Stellar's overlay network and collect consensus related messages. Consensus messages are key to Vault operators as consensus is required to fulfill issue and redeem requests from users.

## Vault Operations

1. **Provide Collateral**  The amount of collateral provided determines how many assets the Vault can accept for safekeeping. &#x20;
2. **Issue**: Vaults receive stable-coins from users for safekeeping. This locks the Vault’s collateral until the stable-coins are redeemed again.
3. **Redeem**: Vaults listen for redeem requests from the Pendulum bridge. Upon receiving such a request, the Vault releases the stable-coins back to the user who issued the request.\
   In order to guarantee the correctness of their behavior, and unlock their own collateral, this operation needs to be proven by the Oracle agents
4. **Replace**: When Vaults want to exit the bridge, they can send a replace request to move their stored assets to another Vault. The other Vault accepts these assets for safekeeping under the condition that it has enough free collateral.
