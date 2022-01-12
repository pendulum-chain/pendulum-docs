# Interacting with the AMM

**Note**: In order for the following steps to work make sure that the account you imported to the Playground has some EUR and USDC on Pendulum. You can check the Pendulum balances in the “BRIDGE” tab.

For demonstration purposes we deployed an automated market maker (AMM) smart contract for the asset pair EUR-USDC to the pendulum chain. You can interact with this smart contract directly through the playground UI. Just click on the “AMM” button at the top.

The first thing you will see is the ‘Swap’ interface. You can use it to trade some of your EUR tokens for USDC or vice versa. To do this, you specify how much you want to receive of an asset and the amount you have to spend for this is calculated and filled in the other text field automatically.

![](<../../.gitbook/assets/image (8).png>)

You can also become a liquidity provider by supplying your USDC and EUR to the pool. Again, you only specify the amount of one asset and the other amount is calculated automatically such that it matches the ratio of the current pool reserves. In return for this operation you receive _liquidity provider tokens_ (LPT) which are used for tracking your contribution to the pool and can later be used to withdraw your share from the pool again.

![](<../../.gitbook/assets/image (6).png>)

If at a later point in time you want to regain your assets from the pool again, you can trade the LPT you received for supplying liquidity to withdraw your share from the pool. The estimated returns you receive for your LPT are shown below the input field.

![](<../../.gitbook/assets/image (5).png>)

You can also always have a look at the stats of the AMM, i.e. the total supply of pool tokens (LPT), your share of the pool and the reserves of the pool. Reserves are similar to the ‘balance’ of the AMM, i.e. the total amount of USDC and EUR that the smart contract holds as supplied liquidity.

![](<../../.gitbook/assets/image (11).png>)
