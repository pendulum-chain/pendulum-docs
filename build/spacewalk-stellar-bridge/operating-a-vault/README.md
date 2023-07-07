---
description: Everything you need to know to set-up and run a Vault for Spacewalk
---

# Operating a Vault client

## Overview

A Vault is an entity that provides bridging utilities to users. It achieves this, by provisioning the underlying infrastructure for bridging tokens.

Users can safely bridge their assets utilizing a Vault. Vaults live between the Stellar network and the Spacewalk-enabled Substrate chains and listen to events on both networks. In order for the Vault to be able to provide its services, the Vault locks up a number of tokens that acts as collateral. This collateral can be provided in a number of pre-defined currencies, e.g. $DOT or $KSM. &#x20;

## Roles

### Vault User

Users that want to bridge assets between Stellar and the Spacewalk-chain (Or Vice versa) use Vaults for doing so. To bridge assets from Stellar, the user would first send the respective amount of assets to the Vault's Stellar account, and then receive the corresponding amount of wrapped assets on the Spacewalk-chain.&#x20;

To un-bridge the wrapped assets again, the user creates a respective request to a Vault, instructing it to release the desired amount back to a specified account on Stellar. The wrapped assets are then burned on the Spacewalk-chain, and the Vault is responsible to do the transfers on Stellar.

When interacting with a Vault, the user gives up the custody of their stablecoins (on Stellar) and incurs the risk of having their valuable assets stolen. However, since the Vault is over-collateralized the Vault itself is not incentivized to 'steal' assets from the user because they get punished for doing so by slashing their collateral. Vaults might choose to steal the locked assets only in case of significant price drops and liquidity shortages.  In that case, users will be reimbursed **only with the asset the Vault has collateralized** - not the currency they initially started out with.

### Vault Operator

Vaults receive custody of assets from their users and inherently make a bet that the prices of assets they collateralize with will either stay constant or increase in value against stablecoin. Upon receiving custody of the assets they will release an equivalent amount of PEN tokens to allow users to operate.

Vaults have to release the user's locked tokens on Stellar when users decide to redeem their coins, ie. when they want to un-bridge them from the Substrate chain.

### Oracle Agents / Relayers

{% hint style="info" %}
Do note that currently, oracle agents are implemented as part of the Vault client although this is not necessary from an architectural point of view.
{% endhint %}

Oracle agents are nodes that listen to Stellar's overlay network and collect consensus-related messages. Consensus messages are key to Vault operators as consensus is required to fulfill issue and redeem requests from users.

## Vault Operations

1. **Provide Collateral**  The amount of collateral provided determines how many assets the Vault can accept for safekeeping. &#x20;
2. **Issue**: When users want to bridge assets to the Spacewalk-chain, they select a Vault that supports this asset, create a new issue request on that chain (targeting the selected Vault) and then transfer the respective amount of stablecoins to that Vault's Stellar account. The issued amount is counted against the Vaults provided collateral to ensure that the Vault is still over-collateralized against the assets it holds. The Vault then ensures that the amount of wrapped tokens is minted on the Spacewalk-chain.
3. **Redeem**: Vaults listen for _redeem_ requests emitted on the Spacewalk-chain. Upon receiving such a request, the vault releases the stablecoins back to the user who issued the request on Stellar.
4. **Replace**: When Vaults want to exit the Spacewalk 'ecosystem', they can send a _replace_ request to move their locked assets to another Vault. The other Vault accepts these assets for safekeeping under the condition that it has enough free collateral.

In order to guarantee the correctness of these operations, the transactions related to issue, redeem, and replace operations needs to be proven to the stellar-relay oracle pallet on the Spacewalk-chain.&#x20;
