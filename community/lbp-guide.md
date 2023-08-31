---
description: Guide on how to participate in the AMPE/KSM LBP.
---

# LBP Guide

### How to contribute to the AMPE/KSM LBP?

**Note → You would need some AMPE tokens as gas for executing this extrinsic**

1. Go to [https://polkadot.js.org/apps/](https://polkadot.js.org/apps/) and switch to Amplitude network from the network menu or directly click on this [link](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Famplitude-rpc.dwellir.com#/explorer).
2. Find `Developer` in the top menu, and choose `Extrinsics` from the drop down
3.  You will be on the following page, see screenshot below.

    ![Screenshot 2023-08-29 at 4.45.45 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3c9bb2c4-5ab3-49d4-bc49-d6f97d8c0b40/Screenshot\_2023-08-29\_at\_4.45.45\_PM.png)
4. Now choose the account you want to contribute from from the field “**using the selected account”**
5. Next in the “**Submit the following extrinsic**” dropdown choose “**`zenlinkProtocol`**”
6. In the next dropdown choose “**`bootstrapContribute(asset0, asset1, amount0Contribute, amount1Contribute, deadline)`**”
7. Now a list of fields would appear below.
8. In the asset0 section → This is for the AMPE token
   1. `chainId` should be 2124
   2. `assetType` should be 0
   3. `assetIndex` should be 0
9. In the `asset1` section → This is for the KSM token
   1. `chainId` should be 2124
   2. `assetType` should be 2
   3. `assetIndex` should be 256
10. In `amoun0Contribute`, enter the amount you want to contribute for AMPE. Make sure to add `12` zeros to your amount. For ex. if you wish to contribute `10` then the input should be `10000000000000`
11. In `amoun1Contribute`, enter the amount you want to contribute for KSM. Make sure to add `12` zeros to your amount. For ex. if you wish to contribute `10` then the input should be `10000000000000`
12. For `deadline` field, add the block number that is 5 blocks higher than the current block-number. For ex. current block number is 10 then add 5 so the input should be 15. Current blocknumber can be found in the top menu **Network > Explorer**
13. Now click on the “Submit Transaction” at the bottom of the screen.
14. Now from the pop-up click “Sign and Submit”. Next, enter your password in the wallet pop-up and confirm the transaction.
15. Once done, if the contribution is successful on polkadot.js screen you will see a green confirmation in the top right corner.

### How to claim the LP tokens?

Note: This is to be done once the LBP contribution period ends.

1.  Follow steps 1,2 and 3 from this section [How to contribute to the AMPE/KSM LBP?](https://www.notion.so/How-to-contribute-to-the-AMPE-KSM-LBP-4f38580fce004261b052d323f096b711?pvs=21)

    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/462fec00-8a37-4e5c-a168-4fae178210da/Untitled.png)
2. Now choose the account you want to sign this transaction from the field “**using the selected account”**
3. Next in the “**Submit the following extrinsic**” dropdown choose “**`zenlinkProtocol`**”
4. In the next dropdown choose “`**bootstrapClaim(recipient, asset0, asset1, deadline)**`”
5. Now a list of fields would appear below.
6. In the `recipient` dropdown select “Id”
7. Now in the AccounId dropdown select the account you used for contributing to the LBP
8. In the `asset0` section → This is for the AMPE token
   1. `chainId` should be 2124
   2. `assetType` should be 0
   3. `assetIndex` should be 0
9. In the `asset1` section → This is for the KSM token
   1. `chainId` should be 2124
   2. `assetType` should be 2
   3. `assetIndex` should be 256
10. In the `deadline` field, Add the block number that is 5 blocks higher than the current block-number. For ex. current block number is 10 then add 5 so the input should be 15. Current blocknumber can be found in the top menu **Network > Explorer**
11. Now click on “Submit Transaction” from the bottom of the screen.
12. Now from the pop-up click “Sign and Submit”. Next enter your password in the wallet pop-up and confirm the transaction.
13. Once done, if the contribution is successful on polkadot.js screen you will see a green confirmation in the top right corner.
