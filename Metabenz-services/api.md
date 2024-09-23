---
description: Integrate your product to your community and token trough the Studio API.
---

# Studio API

## METABENZ Network-studio-backend v0.1.0

The METABENZ Network Network Studio REST API for accessing the data and the services of the METABENZ Network Network network in a simple way. You can use this API to query and interact with the objects of the METABENZ Network Network network such as: Communities, Tokens, Bridges and Entities.

## Bridge

### Fetch bridge

The token bridge connects the Ethereum and METABENZ Network Network network

```text
GET /bridges/:homeTokenAddress
```

#### Parameter Parameters

| Name             | Type     | Description                              |
| :--------------- | :------- | :--------------------------------------- |
| homeTokenAddress | `String` | Home \(METABENZ Network Network\) token address |

#### Success 200

| Name                     | Type     | Description                                                   |
| :----------------------- | :------- | :------------------------------------------------------------ |
| homeTokenAddress         | `String` | Token address on the METABENZ Network Network network                |
| foreignTokenAddress      | `String` | Token address on the Ethereum network                         |
| foreignBridgeAddress     | `String` | Bridge address on the Ethereum network                        |
| homeBridgeAddress        | `String` | Bridge address on the METABENZ Network Network network               |
| homeBridgeBlockNumber    | `Number` | Bridge creation block number on the METABENZ Network Network network |
| foreignBridgeBlockNumber | `Number` | Bridge creation block number on the Ethereum network          |

## Community

### Add plugins to community

```
POST /communities/:communityAddress
```

#### Parameter Parameters

| Name             | Type     | Description                    |
| :--------------- | :------- | :----------------------------- |
| communityAddress | `String` | Community address              |
| plugins          | `Object` | The plugins \(with arguments\) |

#### Param Examples

`json` - Request-Example:

```javascript
{
  "plugins": {
     "businessList": {
         "isActive": true,
      },
     "joinBonus": {
         "isActive": false,
         "hasTransferToFunder": false
     },
  }
}
```

### Fetch community

Community is a set of contracts and services. Members of the community are users of the METABENZ Network Network network. The community is configured via the plugins.

```text
GET /communities/:communityAddress
```

#### Parameter Parameters

| Name             | Type     | Description       |
| :--------------- | :------- | :---------------- |
| communityAddress | `String` | Community address |

#### Success 200

| Name                 | Type      | Description                                                                                          |
| :------------------- | :-------- | :--------------------------------------------------------------------------------------------------- |
| communityAddress     | `String`  | Address of the community on the METABENZ Network Network network                                            |
| homeTokenAddress     | `String`  | Address of the community token on the METABENZ Network Network network                                      |
| foreignTokenAddress  | `String`  | Address of the community token on the Ethereum network                                               |
| homeBridgeAddress    | `String`  | Address of the community bridge on the METABENZ Network Network network                                     |
| foreignBridgeAddress | `String`  | Address of the community bridge on the Ethereum network                                              |
| isClosed             | `Boolean` | Is the community is closed or open. Closed community requires an approve of community admin to join. |
| plugins              | `Object`  | Defines the community plugins.                                                                       |

## Entity

### Fetch my communities

Fetching communities I'm part of

```text
GET /entities/account/:account
```

#### Parameter Parameters

| Name    | Type     | Description |
| :------ | :------- | :---------- |
| account | `String` | address     |

#### Success 200

| Name | Type       | Description                                        |
| :--- | :--------- | :------------------------------------------------- |
| -    | `Object[]` | List of entities with their communities and tokens |

### Fetch community entities

```
GET /entities/:communityAddress
```

#### Parameter Parameters

| Name             | Type      | Description                                        |
| :--------------- | :-------- | :------------------------------------------------- |
| communityAddress | `String`  | Community address of the METABENZ Network Network network |
| page             | `Number`  | Page number for pagination                         |
| withMetadata     | `Boolean` | Get entities with entity's metadata                |
| search           | `String`  | Entity's name for a search by name                 |

#### Success 200

| Name | Type       | Description                                                |
| :--- | :--------- | :--------------------------------------------------------- |
| -    | `Object[]` | List of entities. See GetEntity endpoint for entity fields |

### Fetch entity

Entity is an account on the METABENZ Network Network network. It can have variety of roles like user, admin, business, or custom defined role.

```text
GET /entities/:communityAddress/:account
```

#### Parameter Parameters

| Name             | Type     | Description              |
| :--------------- | :------- | :----------------------- |
| communityAddress | `String` | Community address        |
| account          | `String` | Entity's account address |

#### Success 200

| Name             | Type      | Description                                   |
| :--------------- | :-------- | :-------------------------------------------- |
| account          | `String`  | Entity's account on METABENZ Network Network network |
| communityAddress | `String`  | Community address of the entity               |
| uri              | `String`  | IPFS URI points to entity's metadata          |
| name             | `String`  | Entity's name                                 |
| roles            | `String`  | Entity's role encoded as a byte array         |
| type             | `String`  | Entity's type                                 |
| isAdmin          | `Boolean` |                                               |
| isApproved       | `Boolean` |                                               |

## Token

### Fetch token

Tokens are compatible with the METABENZ Network20 standard, and they also can be burnable/mintable. Tokens are an important part of the community economy.

```text
GET /tokens/:address
```

#### Parameter Parameters

| Name    | Type     | Description   |
| :------ | :------- | :------------ |
| address | `String` | Token address |

#### Success 200

| Name           | Type     | Description                                                          |
| :------------- | :------- | :------------------------------------------------------------------- |
| address        | `String` | Token's address                                                      |
| name           | `String` | Token's name                                                         |
| symbol         | `String` | Token's symbol                                                       |
| tokenURI       | `String` | IPFS URI points to token metadata                                    |
| totalSupply    | `String` | Token's total supply                                                 |
| owner          | `String` | Token's owner                                                        |
| factoryAddress | `String` | Factory contract that created the token                              |
| blockNumber    | `String` | Block number of the token's creation                                 |
| tokenType      | `String` | Token type: basic/mintableBurnable/imported                          |
| networkType    | `String` | Network type where the token is issued: mainnet/ropsten/METABENZ Network |

### Fetch tokens

```
GET /tokens
```

#### Parameter Parameters

| Name        | Type     | Description                  |
| :---------- | :------- | :--------------------------- |
| networkType | `String` | mainnet/ropsten/METABENZ Network |
| page        | `Number` | Page number for pagination   |

#### Success 200

| Name | Type       | Description                                            |
| :--- | :--------- | :----------------------------------------------------- |
| -    | `Object[]` | List of Tokens. See GetToken endpoint for token fields |

### Fetch tokens by owner

```
GET /tokens/owner/:owner
```

#### Parameter Parameters

| Name        | Type     | Description                        |
| :---------- | :------- | :--------------------------------- |
| owner       | `String` | account address of the token owner |
| networkType | `String` | mainnet/ropsten/METABENZ Network       |

#### Success 200

| Name | Type       | Description                                            |
| :--- | :--------- | :----------------------------------------------------- |
| -    | `Object[]` | List of Tokens. See GetToken endpoint for token fields |
