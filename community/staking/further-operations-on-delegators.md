# Further Operations on Delegators

## Increasing and decreasing stakes

1. Navigate to the extrinsics tab and select the respective action
2. Insert the delegator-id to which a user has already delegated and the amount to change

<figure><img src="../../.gitbook/assets/Screenshot_2022-11-16_at_15.45.48.png" alt=""><figcaption></figcaption></figure>

The new stake will be PreviousStake **± amount**

## Leaving delegator

1. Navigate to the extrinsics tab
2. Select the `leaveDelegators()` action
3. Submit the Transaction

## Unlocking Tokens

Before you can unlock your previously staked tokens, you have to wait 7 days (in block time):

1. Navigate to the extrinsics tab
2. Select the appropriate extrinsic: `parachainStaking -> unlockUnstaked(target)`
3. Select the `Id` option (the _MultiAddress field_)
4. Select the address you delegated from (_Id: AccountId_ field)
5. Sign and submit the extrinsic (_Submit Transaction_ button)

Before:&#x20;



<figure><img src="../../.gitbook/assets/Screenshot_2022-11-17_at_11.59.37.png" alt=""><figcaption></figcaption></figure>

After:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot_2022-11-17_at_12.00.41 (1).png" alt=""><figcaption></figcaption></figure>
