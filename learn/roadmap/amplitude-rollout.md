# Amplitude rollout

Amplitude the canary network of its sister blockchain Pendulum.

It will act as a testing ground for applications and network parameters for Pendulum. Unlike a traditional testnet, users can interact on the Amplitude chain with real financial consequences. Lots of novel ways of utilizing fiat on DeFi can be experimented with. Amplitude chain will be powered by its native AMPE token.

### Amplitude Rollout

Amplitude has a phased rollout plan. From sudo to democracy listed below.&#x20;

#### Amplitude Genesis ✅

On 11th August 2022, the Amplitude parachain goes [live on Kusama](https://medium.com/pendulum-chain/amplitude-the-rollout-1ddc51a3f68f) and starts producing blocks.

Until the road to democratization process is complete, governance is controlled by a sudo account. The sudo account is a multi-sig account controlled by the Pendulum foundation to issue transactions and runtime upgrades. Token transfers are not yet enabled.

#### Distribute Crowdloan Rewards

Crowdloan AMPE rewards are distributed to the individual Amplitude accounts that contributed to the [crowdloan](https://parachains.info/auctions/kusama-42-47).

#### Distribute Ecosystem Funds

The vesting of the rest of the ecosystem funds gets distributed. The breakdown can be found [here](https://pendulum.gitbook.io/pendulum-docs/get-started/token-economics).

#### Burning Rewards (Referenda #1)

The Substrate pallet that we are using for collator and delegator staking requires the rewards to be minted new. However, our max supply of 200m AMPE tokens were minted in the genesis block. Therefore, in order to maintain constant token supply we want to burn the allocation of collator rewards and mint them anew. We will have a referenda to vote on this.

#### Introduce Treasury

Implementation of the treasury pallet and its configuration is completed through a runtime upgrade.

#### Introduce LDPoS

LDPoS gets introduced to Amplitude. Both collator and delegator staking can go live after this is in place.

#### Remove Sudo (Referenda #2)

Sudo gets removed via a runtime upgrade and from here on the on-chain governance is completely live and fully functional.

#### Enable token transfers

Token transfers, previously blocked, will be enabled here.
