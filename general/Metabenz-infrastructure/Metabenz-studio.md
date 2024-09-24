# METABENZ Network Studio

## Backend Infrastructure

The backend is composed of the following independent services

* Studio API Backend has two purposes. Provides an API for fast and convenient querying of the blockchain data for the Studio DApp. Transmits heavy and complicated transaction flows on behalf of the user.
* METABENZ  Network-funder service used to fund community members and wallet users on the METABENZ  Network blockchain.
* METABENZ  Network IPFS proxy used for fast fetching and storing data in IPFS.

## Contracts

METABENZ Network  studio is designed to launch DeFi communities on the METABENZ Network . The community contract binds together most of the services and features of the Studio. Among other things it consists of:

* Entities List contract to store community members and their roles
* Community ERC20 tokens on METABENZ Network  with transfer rules
* ERC20 tokens on Ethereum. This is the token that the user issues as part of the community deployment process
