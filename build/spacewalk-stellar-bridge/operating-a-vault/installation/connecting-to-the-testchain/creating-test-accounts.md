# Creating test accounts

## Prerequisite

The vault client needs access to two accounts:&#x20;

* a Substrate account;
* a Stellar account.

While testing, you can use a set of default development accounts which are pre-funded in the genesis configuration of the chain spec.

In order to do so, you can run the vault with the "alice" keyring:

{% code overflow="wrap" lineNumbers="true" %}
```bash
 # These paths assume you are in the root of the provided github repo
 cargo run --bin vault --features standalone-metadata -- --keyring alice [...]
```
{% endcode %}

## Stellar Configuration

On the stellar account, in order to issue tokens it is necessary to have a trustline to the assets you want to bridge. For the testnet, the asset we test with is the following USDC asset:

`GAKNDFRRWA3RPWNLTI3G4EBSD3RGNZZOY5WKWYMQ6CQTG3KIEKPYWAYC:USDC`

On Stellar, we need to have a funded testnet account that has a trustline to our pre-configured USDC testnet asset. The issuer of this testnet asset was chosen arbitrarily but is now hard-coded so it is important that you use this asset. To create and fund this Stellar account as well as for adding the trustline you can use Solar wallet.

### Adding a trustline for your bridged asset

**XLM** tokens can simply be bridged without any setup from the testnet account

If you want to bridge **assets besides XLM** you first have to add a trustline for that asset to your Stellar account. You can follow the [stellar guide ](https://developers.stellar.org/docs/fundamentals-and-concepts/stellar-data-structures/accounts#trustlines)to setting up a Trustline with the following USDC asset if you want to test issuing USDC:

`GAKNDFRRWA3RPWNLTI3G4EBSD3RGNZZOY5WKWYMQ6CQTG3KIEKPYWAYC:USDC`

If you are using Solar wallet, you can find instructions on how to add a trustline [here](https://docs.solarwallet.io/guide/07-asset-management.html#add-custom-assets).

