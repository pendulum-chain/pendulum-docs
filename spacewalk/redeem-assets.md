---
description: Move tokens from testchain to Stellar
---

# Redeem assets

Finally you can redeem your assets back to Stellar. To do so:

1. Go to [https://prototype-ui.pendulumchain.org/?rpc=ws://127.0.0.1:9944#/extrinsics](https://prototype-ui.pendulumchain.org/?rpc=ws://127.0.0.1:9944#/extrinsics)
2. Select your User Account, and then select `spacewalk` from the first dropdown.
3. From the second dropdown, select the `redeem(assetCode, assetIssuer, amount, stellarVaultPubkey)` extrinsic
4. Set the `assetCode` to **`USDC`**, `assetIssuer` to **`GAKNDFRRWA3RPWNLTI3G4EBSD3RGNZZOY5WKWYMQ6CQTG3KIEKPYWAYC`**, `amount` to **`1000000000000`** (since this is a Balance field, we need to provide the actual number including the decimal places, this number is equivalent to 1 Unit).
5. For `stellarVaultPubkey` you will need to provide the binary version of your Vault Account's public key – that means that you can't use the string encoding starting with `GDR....` No worries, to obtain the hex encoded representation of your public key, you can use our converter. Just go to [https://prototype.pendulumchain.org/](https://prototype.pendulumchain.org), and click on `Tools` In the topbar. In the modal that appears paste your Stellar pubkey and you'll see the different address formats. Below the `Raw bytes` section you should get something like`0x3d91b2350cce8449f51ff31156fe9d8770b8fa993a500069be7bac2f861151c3`. That's the value you need.
6. Submit the transaction
7. Check that the redeem was successfully executed:\
   \- Check the balances of your imported test stellar account. It should have received `1 USDC`.\
   ``- The Vault logs should print something similar to this

```
INFO vault::redeem: Received redeem request: Redeem { asset_code: [85, 83, 68, 67], asset_issuer: [71, 65, 75, 78, 68, 70, 82, 82, 87, 65, 51, 82, 80, 87, 78, 76, 84, 73, 51, 71, 52, 69, 66, 83, 68, 51, 82, 71, 78, 90, 90, 79, 89, 53, 87, 75, 87, 89, 77, 81, 54, 67, 81, 84, 71, 51, 75, 73, 69, 75, 80, 89, 87, 65, 89, 67], stellar_user_id: [109, 129, 185, 73, 159, 66, 76, 36, 66, 10, 98, 117, 247, 128, 98, 227, 97, 129, 113, 211, 86, 76, 124, 74, 99, 228, 234, 42, 213, 76, 196, 88], stellar_vault_id: [61, 145, 178, 53, 12, 206, 132, 73, 245, 31, 243, 17, 86, 254, 157, 135, 112, 184, 250, 153, 58, 80, 0, 105, 190, 123, 172, 47, 134, 17, 81, 195], amount: 1000000000 }
INFO vault::redeem: Executing redeem Redeem { asset_code: [85, 83, 68, 67], asset_issuer: [71, 65, 75, 78, 68, 70, 82, 82, 87, 65, 51, 82, 80, 87, 78, 76, 84, 73, 51, 71, 52, 69, 66, 83, 68, 51, 82, 71, 78, 90, 90, 79, 89, 53, 87, 75, 87, 89, 77, 81, 54, 67, 81, 84, 71, 51, 75, 73, 69, 75, 80, 89, 87, 65, 89, 67], stellar_user_id: [109, 129, 185, 73, 159, 66, 76, 36, 66, 10, 98, 117, 247, 128, 98, 227, 97, 129, 113, 211, 86, 76, 124, 74, 99, 228, 234, 42, 213, 76, 196, 88], stellar_vault_id: [61, 145, 178, 53, 12, 206, 132, 73, 245, 31, 243, 17, 86, 254, 157, 135, 112, 184, 250, 153, 58, 80, 0, 105, 190, 123, 172, 47, 134, 17, 81, 195], amount: 1000000000 }
INFO vault::redeem: Sending request to: <https://horizon-testnet.stellar.org/accounts/GA6ZDMRVBTHIISPVD7ZRCVX6TWDXBOH2TE5FAADJXZ52YL4GCFI4HOHU>
INFO vault::redeem: Submitting transaction to Stellar network: <https://horizon-testnet.stellar.org/transactions>, tx_xdr: "AAAAAgAAAAA9kbI1DM6ESfUf8xFW/p2HcLj6mTpQAGm+e6wvhhFRwwAAJxAAAgCaAAAAGAAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAQAAAABtgblJn0JMJEIKYnX3gGLjYYFx01ZMfEpj5Ooq1UzEWAAAAAFVU0RDAAAAABTRljGwNxfZq5o2bhAyHuJm5y7HbKthkPChM21IIp+LAAAAAAAAJxAAAAAAAAAAAYYRUcMAAABAvbbpXEBOWNCphlZHwy68uJclBLVCyiVXwnQ65lXfklWGYhYAJeUAAe+NSsgeLwEIPiyHFj42mycPXsl3X3xDDw=="
INFO vault::redeem: Transaction submitted to Stellar network: Response { url: Url { scheme: "https", cannot_be_a_base: false, username: "", password: None, host: Some(Domain("horizon-testnet.stellar.org")), port: None, path: "/transactions", query: None, fragment: None }, status: 200, headers: {"date": "Thu, 21 Apr 2022 09:31:57 GMT", "content-type": "application/hal+json; charset=utf-8", "transfer-encoding": "chunked", "connection": "keep-alive", "cache-control": "no-cache, no-store, max-age=0", "content-disposition": "inline", "vary": "Origin"} }
INFO vault::redeem: ✔️  Successfully submitted withdrawal transaction to Stellar, crediting GBWYDOKJT5BEYJCCBJRHL54AMLRWDALR2NLEY7CKMPSOUKWVJTCFQFYI
INFO vault::redeem: Completed redeem request with amount 1000000000
```
