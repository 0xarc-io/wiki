---
description: A brief guide on how to use our endpoints.
---

# 🧠 API

## Getting started

Integrating scores into your own dApp requires no sign-ups nor registrations. We provide open APIs to encourage the use of scores (i.e. address reputation) across the DeFi ecosystem.



If you'd like to create and integrate your own score, we'd love to help you with that ! \
[Contact us on discord](https://discord.com/invite/skwz6je)



Here's the step-by-step for developers to integrate scores into their smart contracts:

#### 1. Get your Score Proof

First, you'll need to fetch a specific score of a specific user. Let's say the score you want to fetch is `arcx.loyalty` and the wallet address is `0x123...456`. You would then simply make the following API call using the language/framework of your choosing:

```
https://api.arcx.money/scores/0x123...456/arcx.loyalty
```

This will return your score containing a Merkle proof. We'll refer to this object as the **Score Proof.** [Here's an example](api.md#get-scores-address-score-score-proof) of what that looks like.&#x20;

#### 2. Send your Score Proof to a smart contract

With your Score Proof, you now have everything you need and can call a smart contract. Simply include this proof into a your on-chain call to verify it in solidity/smart contracts. If there is a `metadata` field in your Score Proof, simply drop it (it is not needed on-chain).

#### 3. Verify your Score Proof

Once the proof is in smart-contract code, simply [verify it using our contracts](smart-contracts.md#verifying-a-score) to ensure its integrity. Once verified, you can add your own rules and logic.

#### 4. Custom Score logic

Now that your score is verified, the fun begins! You can write any smart-contract logic based on the value of the score. Here's [some examples](../introducing-arcx/faqs.md#what-problem-is-arcx-solving) of what problems can now be solved.



For further questions, explanations or examples, come chat with us on [discord](https://discord.com/invite/skwz6je).

## Scores endpoints

### GET /scores/:address

Get all the scores of a specific address. This will include all the scores in our system for this address, even those that the address does not yet have.

When an address does not have a score, its `score` will be `null`.

Example:

```
https://api.arcx.money/scores/0x123...456
```

Response:

```
[
    {
        "account": "0x123...456",
        "protocol": "0x611...000",
        "score": "100",
        "merkleProof": [
            "0x111...111",
            "0x222...222",
            "0x333...333",
            ...,
        ],
        "metadata": {
            ...
        },
    },
    {
        "account": "0x123...456",
        "protocol": "0x622...000",
        "score": "500",
        "merkleProof": [
            "0xaaa...aaa",
            "0xbbb...bbb",
            "0xccc...ccc",
            ...,
        ],
        "metadata": {
            ...
        },
    },
    {
        "account": "0x123...456",
        "protocol": "0x633...000",
        "score": null,
        "merkleProof": [],
    },
    {
        ...
    }
]
```

### GET /scores/:address/:score - (Score Proof)

A more precise option from the previous `/scores/:address` endpoint. Most effective method of obtaining the required Score Proof for[ on-chain use.](smart-contracts.md#verifying-a-score)

Example:

```
https://api.arcx.money/scores/0x123...456/arcx.loyalty
```

Response:

```
 {
    "account": "0x123...456",
    "protocol": "0x611...000",
    "score": "175",
    "merkleProof": [
        "0x111...111",
        "0x222...222",
        "0x333...333",
        ...,
    ],
    "metadata": {
        ...
    },
}
```

## Passports endpoints

### GET /passports

List all the addresses who have claimed their Passport alongside the date they claimed.

Example:

```
https://api.arcx.money/passports
```

Response:

```
[
    {
        "address": "0x111...111",
        "date_claimed": 1641184343323
    },
    {
        "address": "0x222...222",
        "date_claimed": 1641136874287
    },
    {
        "address": "0x333...333",
        "date_claimed": 1641132310215
    },
    {
        "address": "0x444...444",
        "date_claimed": 1641137470422
    },
    ...
]
```



## Help

If you have any questions or suggestions, we'd love your input in our [Discord](https://discord.com/invite/skwz6je).\
\
Happy building! ノ

****
