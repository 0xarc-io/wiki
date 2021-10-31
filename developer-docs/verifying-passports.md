---
description: A brief guide on using the ARCx API
---

# API

## Introduction

The ARCx team provides a variety of endpoints to 3rd-party developers to facilitate the acquisition of data related to ARCx products. Most of the information returned by our endpoints can also be parsed from on-chain logs. There are three main categories to our endpoints:

* [Reputation](verifying-passports.md#reputation) : The ARCx infrastructure creates on-chain reputation data for a variety of addresses. Such data is used by 3rd party developers and the ARCx Passport (see below) to make data-driven decisions on-chain. Here you can fetch the list of indexed addresses, view a  reputation profile and fetch a proof of a particular score within a profile for [on-chain verification.](smart-contracts.md)&#x20;
* [Passports](verifying-passports.md#passports) : The ARCx Passport is they key to the ARCx ecosystem. It enables staking, borrowing and skin features. This NFT is a visual representation of your blockchain identity, but does not provide any benefit outside the ARCx ecosystem.
* [Protocols](verifying-passports.md#protocols) : ARCx has a variety of scores and partnerships with other dApps. These endpoints allow for transparency is who is integrated with ARCx and which scores are currently being indexed.&#x20;

CURRENT API VERSION: `v1.0`

```
https://api.arcx.money
```

## Reputation



### GET /reputation

Get the list of all addresses currently being indexed by the ARCx protocol.

Example:

```
https://api.arcx.money/reputation
```

Response:

```
[
    "0xE4F...90B",
    "0x9c7...89b",
    "0xcd7...A1E",
    ...
]
```

### GET /reputation/:address

Get the entire reputation profile of a specific address. This will be an array of objects outlining all the potential score this address could obtain.



To verify each score on the blockchain, simply drop the `metadata` attribute and use the remainder 4 attributes (`account`, `protocol`, `score` and `merkleProof`) to [verify the score on the blockchain](smart-contracts.md).

Example:

```
https://api.arcx.money/reputation/0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E
```

Response:

```
[
    {
        "account": "0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E",
        "protocol": "0x617263782e6c6f79616c74790000000000000000000000000000000000000000",
        "score": "175",
        "merkleProof": [
            "0xedb1ef66264d930648d442114717dec9b83dbdf7cfee95d39822a7b0bb262ffc",
            "0xc21773776d32c50291589cfda4c1ff545ba30376974eb7388633cd420456341e",
            "0xc803198ff567cb0359896bbf26d7b5daafc74e00a2314acd3938e85b10a490d6",
            "0x8294acc477326db80c02ad7c50c40f56580ef3933a5155b5929c7297176b0b94",
            "0xffe33ed76230c01bce31bfcee95bf010c3c926fcb52350479b95a4a54f5005c6",
            "0x505a53ea980962e958e9cadd79a8d26bb3431de6d1d3dd84ed816be6f3d38d47"
        ],
        "metadata": {
            "name": "arcx.loyalty",
            "maxValue": "450",
            "minValue": "50",
            "description": "This score is calculation based on your interactions (positive or negative) with the ARCx protocol.",
            "title": "ARCx Loyalty Score",
            "externalURI": "",
            "sources": ["ethereum"],
            "explanations": [
                {
                    "value": "+50",
                    "key": "Participated in an ARCx Farm"
                },
                ...
            ],
            "suggestions": {
                "account": [
                    "Stake your ARCx tokens.",
                    ...
                ],
                "global": [
                    "Stay active within the Discord community",
                    ...
                ]
            },
        }
    },
    {
        ...
    }
]
```

####

### GET /reputation/:address/:score - (Merkle Proof)

A more precise option from the previous `/reputation/:address` endpoint. Most commonly used by 3rd party developers to verify their respective user's scores.

This is the **exact** format needed to [verify scores on the blockchain](smart-contracts.md). Scores are verified using Merkle Trees, more information regarding this topic can be found [here](https://en.wikipedia.org/wiki/Merkle\_tree).

Example:

```
https://api.arcx.money/reputation/0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E/arcx.loyaltyty
```

Response:

```
{
    "account": "0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E",
    "score": "175",
    "protocol": "0x617263782e6c6f79616c74790000000000000000000000000000000000000000",
    "merkleProof": [
        "0xedb1ef66264d930648d442114717dec9b83dbdf7cfee95d39822a7b0bb262ffc",
        "0xc21773776d32c50291589cfda4c1ff545ba30376974eb7388633cd420456341e",
        "0xc803198ff567cb0359896bbf26d7b5daafc74e00a2314acd3938e85b10a490d6",
        "0x8294acc477326db80c02ad7c50c40f56580ef3933a5155b5929c7297176b0b94",
        "0xffe33ed76230c01bce31bfcee95bf010c3c926fcb52350479b95a4a54f5005c6",
        "0x505a53ea980962e958e9cadd79a8d26bb3431de6d1d3dd84ed816be6f3d38d47"
    ]
}
```



## Passports

The ARCx Passport is an ERC721 that is non-transferable and unique to each address.

### GET /passports/:address

Each Passport has accessible metadata, including one of the following statuses:

* `active`: This address has an active ARCx Passport and already can use its benefits.
* `unclaimed`: This address has yet to claim it's Passport, but it can do so at any time.
* `waitlist` : This address will be able to claim its Passport soon.
* `untracked` : This address is not indexed by ARCx in any way.
* `burnt` : This address is blacklisted from ever having a Passport.

Example:

```
https://api.arcx.money/passports/0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E
```

Response:

```
{
    "address": "0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E",
    "status": "active",
    "dateIssued": 1629412046,
    "tokenId": 3,
    "activeSkin": {
        "title": "ARCx Default White",
        "description": "ARCx Default DeFi Passport Skins. Comes in black, purple and white.",
        "tokenIds": ["3"],
        "contract": "0x302434B8676048b9FDE0aD20952999C84c7f1428",
        "group": "arcx",
        "name": "white",
    }
}
```

### GET /passports/eligible/:address

To receive an ARCx Passport, an address is required to meet certain on-chain criteria. These are defined below, and may change over time. However, even if eligibility requirements change, once an address claims its Passport, it cannot be revoked.

Example:

```
https://api.arcx.money/passports/eligible/0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E
```

Response:

```
[
    {
        "passed": true,
        "title": "Address History",
        "description": "Total amount of days since first transaction.",
        "required": 30,
        "current": 130
    },
    {
        "passed": true,
        "title": "Gas Spent (ETH)",
        "description": "Total amount of gas spent (in ETH) since beginning of time.",
        "required": 0.01,
        "current": 0.32
    },
    {
        "passed": true,
        "title": "Unique Interactions",
        "description": "Total unique interactions between all other addresses since beginning of time.",
        "required": 5,
        "current": 10
    }
]
```

## Protocols

### GET /protocols

List all the protocols which are currently integrated with the ARCx ecosystem

Example:

```
https://api.arcx.money/protocols
```

Response:

```
[
    "arcx",
    "polygon",
]  
```

### GET /protocols/:name

List the metadata of a particular protocol which is integrated with the ARCx ecosystem.

Example:

```
https://api.arcx.money/protocols/arcx
```

Response:

```
{
    "registryURI": "https://prod.data.arcx.money/registry",
    "scoresURI": "https://prod.data.arcx.money/scores",
    "scoresMetadata": [
        {
            "name": "arcx.credit",
            "description": "The ARCx quantification of credit worthiness create by analyzing blockchain transactions.",
            "title": "ARCx Credit Score",
            "sources": ["ethereum", "avax", "polygon"],
            "maxValue": "1000",
            "minValue": "0",
            "externalURI": "https://wiki.arcx.money/",
            "suggestions": [
                "Always pay your debts on time",
                "Ensure you have plenty of collatoral in the event of margin calls"
            ]
        },
        {
            "name": "arcx.loyalty",
            "description": "This score is calculation based on your interactions (positive or negative) with the ARCx protocol.",
            "title": "ARCx Loyalty Score",
            "sources": ["ethereum"],
            "suggestions": [
                "Consider staking ARCx",
                "Stay active within the Discord community",
                "HODL the ARCx token",
            ]
        }
    ]
}
```



**If you have any questions or comments, join us on **[**Discord**](https://discord.com/invite/arcx)****

****
