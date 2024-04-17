# Cross-chain transfer KSM

### How to move KSM from relay chain to Amplitude?

1. Go to [https://polkadot.js.org/apps/](https://polkadot.js.org/apps/) and switch to **Kusama** network from the network menu or directly click on this [link](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fksm-rpc.stakeworld.io#/extrinsics/decode)
2. Find `Developer` in the top menu, and choose `Extrinsics` from the drop down. Select the `Decode` tab

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>Top tab</p></figcaption></figure>

3. Paste the below in the field `hex-encoded call`&#x20;

`0x630801000100312101000101004e5d80a091a712b727ecbb00882bb28d4d64a6e7f6c87654b3243c489623f5100104000000000700e876481700000000010300286bee02093d00`

3. Now switch to the `Submission` tab
4. In the `using the selected account` select the account you want to send the KSM from
5. **Now in the beneficiary section in the `id` field, enter your address. Please make sure you have entered your address here, the prefilled address is not your address.**

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

7. Now next in the assets section, enter the amount of KSM you want to transfer in the `Fungible` field. Note - Since there are 12 decimals for the KSM token, you need to add 12 zeros after choosing the KSM amount e.g. If you want to transfer 1 KSM, then you should write `1000000000000`.

<figure><img src="../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

8. Apart from this, you don’t need to change anything in the submission.
9. Now click on the “Submit Transaction” at the bottom of the screen.
10. Now from the pop-up click “Sign and Submit”. Next, enter your password in the wallet pop-up and confirm the transaction.
11. Once done, if the contribution is successful on polkadot.js screen you will see a green confirmation in the top right corner.
