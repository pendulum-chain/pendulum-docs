# Deploying the AMM

Next, we want to deploy the smart contract that we compiled in [compiling-the-contract.md](compiling-the-contract.md "mention") to the Pendulum chain. Therefore, navigate to [playground.pendulumchain.org](https://playground.pendulumchain.org/#/instantiate) and check that "Pendulum Testnet" is selected. Now click on "Add New Contract" in the sidebar and click on the "Upload New Contract Code" button.&#x20;

![](<../../.gitbook/assets/image (17).png>)



Click on the "Upload Contract Bundle" field and choose the `.contract` file you compiled in the previous step. Make sure that "alice" is selected as "Account" and click on "Next".

![](<../../.gitbook/assets/image (11).png>)

Next, you have to fill in the constructor values of the smart contract. For the Pendulum AMM choose:

| Key          | Value                                                    |
| ------------ | -------------------------------------------------------- |
| `assetCode0` | EUR                                                      |
| `issuer0`    | GAKNDFRRWA3RPWNLTI3G4EBSD3RGNZZOY5WKWYMQ6CQTG3KIEKPYWAYC |
| `assetCode1` | USDC                                                     |
| `issuer1`    | GAKNDFRRWA3RPWNLTI3G4EBSD3RGNZZOY5WKWYMQ6CQTG3KIEKPYWAYC |

You can leave the rest of the values as-is. The "Value" is what you are willing to pay for the storage rent and determines how long your smart contract is going to "live" on Pendulum.&#x20;

Once done, click on the "Next" button once again. You now get the chance to review your operation. To submit the transaction that deploys the smart contract click on "Upload and Instantiate" and wait for the submission to finish.

![](<../../.gitbook/assets/image (10).png>)
