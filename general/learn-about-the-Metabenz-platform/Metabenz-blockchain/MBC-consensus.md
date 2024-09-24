# METABENZ  Network Consensus

Consensus refers to the agreement process between nodes in a network. The nodes must agree on which transactions to include in the next block on the chain before these transactions are committed.

There are 2 aspects to the process - the actual consensus mechanism to add transactions to blocks, and Sybil protection and validator incentives.

### Sybil protection and incentives via delegated proof of stake

METABENZ  Network uses delegated Proof of Stake (dPoS) to provide Sybil protection and align the validator incentives.

In order to participate in securing the network consensus, a node operator must stake a minimum required amount of METABENZ Network tokens (currently set at 50k METABENZ Network). Becoming a validator on METABENZ  Network is permissionless, meaning that a node operator just needs to satisfy certain technical requirements. The need to stake METABENZ Network ensures that an entity cannot create multiple seemingly distinct validators without incurring a significant cost. Hence, the Sybil protection. Currently, the maximum number of validators on METABENZ  Network is 100.

The validator who publishes a block agreed upon during a given consensus round is rewarded by the network protocol in newly minted METABENZ Network tokens. They also receive the fees users paid for the transactions included into the block.

Over time, validators can expect to publish a share of blocks equal to their share of the overall stake. Since METABENZ Network uses dPoS, a validator can increase their share by attracting METABENZ Network tokens from delegators.

Validators who violate the consensus rules (by, for instance, not revealing random numbers) can expect their stake (including the delegators' contribution) to be frozen. This provides a strong incentive for validators to behave in the desired manner.
