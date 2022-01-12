# Deploying the AMM

Next, we want to deploy the smart contract that we compiled in [compiling-the-contract.md](compiling-the-contract.md "mention") to the Pendulum chain. Therefore, navigate to [playground.pendulumchain.org](https://playground.pendulumchain.org/#/instantiate) and click on "Instantiate" in the sidebar.&#x20;

![Playground - 'Instantiate' view](<../../.gitbook/assets/image (18).png>)

Click on the "Upload & Instantiate Contract" button and then on the "Upload Contract Bundle" field. Choose the `.contract` file you compiled in the previous step. Make sure that "ALICE" is selected as "instantiation account".

![Playground - Smart contract instantiation](<../../.gitbook/assets/image (2).png>)

Scroll down to the bottom of the page and click on the "> Constructor details" button.&#x20;

Next, you have to fill in the constructor values of the smart contract. For the Pendulum AMM choose:

| Key          | Value                                                    |
| ------------ | -------------------------------------------------------- |
| `assetCode0` | EUR                                                      |
| `issuer0`    | GAKNDFRRWA3RPWNLTI3G4EBSD3RGNZZOY5WKWYMQ6CQTG3KIEKPYWAYC |
| `assetCode1` | USDC                                                     |
| `issuer1`    | GAKNDFRRWA3RPWNLTI3G4EBSD3RGNZZOY5WKWYMQ6CQTG3KIEKPYWAYC |

You can leave the rest of the values as-is. The "Endowment" is what you are willing to pay for the storage rent and determines how long your smart contract is going to "live" on Pendulum.&#x20;

Once done, click on the "Instantiate" button, scroll down to the bottom and click on "Sign & Submit" to submit the transaction that deploys the smart contract.&#x20;
