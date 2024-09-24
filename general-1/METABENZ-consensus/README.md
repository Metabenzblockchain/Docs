# METABENZ Blockchain Consensus

Consensus is a fault-tolerant mechanism that is used in blockchain systems to achieve the necessary agreement on the single state of the network. METABENZ Network  is using a Delegated Proof of Stake (DPoS) consensus model. DPoS is a variation of Proof of Stake consensus. In DPoS there are a set of validators that are responsible for keeping the network updated and validating the network's state. They do this in turns, every validator has their turn in line. On their turn the validator updates the network's state, and the rest of the validators check that the update is valid.

Consensus contract is used to manage the list of the network validators and delegators

BlockReward contract is calculates the reward amount that validators and delegators will receive on each block validation. The reward size is proportional to validator's stake.

With Voting contract validators are vote on various changes on these 3 base level contracts. All those contracts are proxied with implementation that handles the logic. The implementations can be changed only by the Voting process.

The bridge is used to transfer the METABENZ Network  native token between METABENZ Network  and Ethereum networks.

## Consensus - 0x4dCACA64f6CAED26F8553397a99E206ef29e9D26

This contract is responsible for handling the network DPos consensus. The contract stores the current validator set and chooses a new validator set at the end of each cycle. The logic for updating the validator set is to select a random snapshot from the snapshots taken during the cycle.

The snapshots are taken of pending validators, who are those which staked more than the minimum stake needed to become a network validator. Therefore the contract is also responsible for staking, delegating and withdrawing those funds.

Stake amount for a validator is the sum of staked and delegated amount to it's address.

This contract is based on `non-reporting ValidatorSet` described in Parity Wiki.

minimum stake amount = 50k METABENZ  Network Native Coin

cycle duration blocks = 34460 (approximately 2 days)

## Block Reward - 0x7cD40dFd8E122e7D37e986AAA1C0519a337Fa73F

This contract is responsible for generating and distributing block rewards to the network validators according to the network specs (5% yearly inflation).

Another role of this contract is to call the snapshot/cycle logic on the Consensus contract

## Voting - 0xEA0A484E0ba8e5FCA215b876E46c1d4AC658e059

This contract is responsible for opening new ballots and voting to accept/reject them. Ballots are basically offers to change other network contracts implementation.

Only network validators can open new ballots, everyone can vote on them, but only validators votes count when the ballot is closed.

Ballots are opened/closed on cycle end.

max number of open ballots = 100

max number of open ballots per validator = 100 / number of validators

minimum ballot duration (cycles) = 2

maximum ballot duration (cycles) = 14

## Proxy Storage - 0x5B3c8A81aC57B3c819e40D69c954cECDB519b48d

This contract is responsible for holding network contracts implementation addresses and upgrading them if necessary (via voting).
