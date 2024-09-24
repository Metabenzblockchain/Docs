# Stake, Delegate and Withdraw

The basic requirement to become a METABENZ  Network chain validator is to have a stake amount of at least 50k METABENZ  Network . The stake amount is the sum of staked and delegated METABENZ  Network of the address. **Roadmap** - Those functionalities will be built into our Studio and will not require any technical knowledge in the future.

## Stake <a href="#stake" id="stake"></a>

There are two options to stake (both should be called from the address which would be the validator)

1. 1.Send METABENZ  Network to the consensus contract -0x4dCACA64f6CAED26F8553397a99E206ef29e9D26 on the METABENZ  network.
2. 2.Call the \`stake\` function on the consensus contract -0x4dCACA64f6CAED26F8553397a99E206ef29e9D26 on the METABENZ  network.

## Delegate <a href="#delegate" id="delegate"></a>

METABENZ Network  Coin holders who don't want to run a node by themselves but still wish to participate in governing the network can delegate any amount to one of the validators.Delegating is done by calling the \`delegate\` function on the consensus contract (0x4dCACA64f6CAED26F8553397a99E206ef29e9D26) with the validator address as data (see screenshot from MEW).

![delegate](https://3886961007-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MQROvzQPC4eD8u5AQhv%2Fuploads%2FfW2bi43f3TMgmwzi7wSZ%2Fimage.png?alt=media\&token=f30eb8a1-ff40-4f1e-9f73-89466ea2c83e)

## Withdraw <a href="#withdraw" id="withdraw"></a>

Both stakers and validators can withdraw their METABENZ Network , up to the staked/delegated amount, at any time. The withdrawn amount will be deducted from the validator stake amount, and if the stake amount becomes below the minimum stake amount - the validator will be removed from the METABENZ  Network  validators list.There are two options to withdraw:

1. 1.Call the \`withdraw\` function on the consensus contract (0x4dCACA64f6CAED26F8553397a99E206ef29e9D26) with one parameter - the amount to withdraw. This call is for stakers, and will reduce the stake amount of the sender address.
2. 2.Call the \`withdraw\` function on the consensus contract (0x4dCACA64f6CAED26F8553397a99E206ef29e9D26) with two parameters - validator address and amount to withdraw. This call is for both stakers (who can use their own address as the parameter) and for delegators to withdraw their delegated stake on a specific validator.
