# Collateral and Liquidation

## Vault Collateral Asset

A vault can only bridge through one particular collateral. If an owner wants to provide multiple collaterals, they will have to deploy a new vault for each pair.

## Collateral division

Below we define some parameters to help define what elements make up the collateral:

| Type                      | Role                                                                       | Formula                                       |
| ------------------------- | -------------------------------------------------------------------------- | --------------------------------------------- |
| **Used Collateral**       | Currently used collateral                                                  | Backed Tokens \* Secure Threshold             |
| **Backed Tokens**         |                                                                            | Issued Tokens + Tokens to be issued           |
| **Maximum Collateral**    | Maximal amount of stable-coin that can be collateralized                   | Defined on Asset pairs                        |
| **Minimum Collateral**    | Minimal deposit                                                            | <p>30 DOT (Pendulum)<br>3 KSM (Amplitude)</p> |
| **Security Threshold**    | Amount of collateral that enables a vault to store up to X amount of asset | See table                                     |
| **Liquidation Threshold** | Amount of collateral after which the vault will start getting liquidated   | See table                                     |
| **Premium Redeem Factor** | Grants users redeeming at this level a premium on the collateralized asset | See table                                     |

#### Collateral Data for Pendulum

<table><thead><tr><th>Stellar Asset</th><th>Asset</th><th width="200">Security Threshold</th><th>Premium Redeem</th><th>Liquidation</th></tr></thead><tbody><tr><td>USDC</td><td>DOT</td><td>160%</td><td>140%</td><td>125%</td></tr><tr><td>MXN</td><td>DOT</td><td>160%</td><td>140%</td><td>125%</td></tr><tr><td>BRL</td><td>DOT</td><td>160%</td><td>140%</td><td>125%</td></tr><tr><td>XLM</td><td>DOT</td><td>160%</td><td>140%</td><td>125%</td></tr><tr><td>TZS</td><td>DOT</td><td>160%</td><td>140%</td><td>125%</td></tr><tr><td>NGNC</td><td>DOT</td><td>160%</td><td>140%</td><td>125%</td></tr><tr><td>EURC</td><td>DOT</td><td>160%</td><td>140%</td><td>125%</td></tr><tr><td>AUDD</td><td>DOT</td><td>160%</td><td>140%</td><td>125%</td></tr></tbody></table>

#### Collateral Data for Amplitude

| Stellar Asset | Asset | Security Threshold | Premium Redeem | Liquidation |
| ------------- | ----- | ------------------ | -------------- | ----------- |
| USDC          | KSM   | 160%               | 140%           | 125%        |
| MXN           | KSM   | 160%               | 140%           | 125%        |
| BRL           | KSM   | 160%               | 140%           | 125%        |
| XLM           | KSM   | 160%               | 140%           | 125%        |
| TZS           | KSM   | 160%               | 140%           | 125%        |
| NGNC          | KSM   | 160%               | 140%           | 125%        |
| EURC          | KSM   | 160%               | 140%           | 125%        |
| AUDD          | KSM   | 160%               | 140%           | 125%        |

## Liquidation

A Liquidation can happen for a variety of reasons:&#x20;

* The Vault fails to execute a redeem on time
  * In this case the user can either retry with another vault or liquidate a part of the vault
  * The vault is banned from accepting further requests for some time
* The Vault falls below the Liquidation threshold
  * In this case, the entire collateral is liquidated





