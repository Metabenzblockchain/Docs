# Run a METABENZ Validator

## Setting up a node

1. Git clone https://github.com/Metabenzblockchain/Become-Validator.git

2. Create an Account

```
chmod +x openethereum
./openethereum account new --config ./node.toml
```

Returned address like that 0x00ft39d30f0d20ff03a22ccfc30b7efbfca597c2

Copy result address to node.toml
Ex:

```
...
[account]
unlock = ["0x00ft39d30f0d20ff03a22ccfc30b7efbfca597c2"]
password = ["password"]

[mining]
force_sealing = true
engine_signer = "0x00ft39d30f0d20ff03a22ccfc30b7efbfca597c2"
reseal_on_txs = "none"
...
```

3. Run the authority nodes

```
./openethereum --config ./node.toml

```

4. Stake

   Stake

   To stake METABENZ network, all you should do is sending your METABENZ network to the METABENZ Consensus contract address over the METABENZ network from the validator address.
   The METABENZ Consensus contract address: 0x4dCACA64f6CAED26F8553397a99E206ef29e9D26
   The easiest way to do so, is to import your private key or key-store file to your favourite wallet (for example Metamask), switch network to METABENZ and send the METABENZ network to the Consensus contract address.

   You can find your key-store (containing your private key) and the password for the created account in:
   /meta-blockchain/keys/META/UTC--xxxx
   /node.pwd

5. Wait for 1 cycle (approximately 48 hours).

   Wait until the next cycle gets started.