---
description: Move tokens from Stellar to testchain
---

# Issue assets

If you didn't import the User Account and Vault Account to a Stellar wallet yet, you should do it now. Be aware that these are testnet account so you need to import testnet accounts into your wallet.

The User Account should have received 100 USDC, 100 EUR and about 1000 XLM via the _One Click setup_ that we executed while [creating the accounts](creating-test-accounts.md).

1. Send a payment transaction with 10 USDC from the User Account to the Vault Account. The tokens will be locked in the Vault Account and the vault client that we started [previously](running-the-vault.md) will instruct the Spacewalk pallet to mint tokens on _testchain_.
2. After submitting this transaction to Stellar, the logs of the vault client should read something like
3.  ```
    INFO vault::deposit: Found new transaction from Horizon (id "45f690a3041d1d13b2f6cbff9e6654bae27fca0aec73905f7781d59be62e1107"). Starting to process new transaction
    INFO vault::deposit: Reported Stellar transaction to spacewalk pallet
    ```

    and the logs of the test chain should output

    ```
    ✅ Deposit successfully Executed
    ```
4. You can check that your test account has received the 10 USDC by going to [https://prototype-ui.pendulumchain.org/](https://prototype-ui.pendulumchain.org/?rpc=ws://127.0.0.1:9944#/accounts) accounts page and checking for the balance change, it also should appear in the Events section of the explorer.

You can also send some EUR tokens from the User Account to the Vault Account following similar steps in order to issue EUR tokens on _testchain_.
