---
description: How ARCx products work on the blockchain
---

# Smart Contracts

### Introduction

The ARCx infrastructure is built on [Merkle trees](https://www.investopedia.com/terms/m/merkle-tree.asp) to maintain good security and scalability standards. Therefore, there are two concepts that are important to grasp:

* **Epoch**: We update our Merkle tree every epoch (i.e. a set period of time, 24h, 1 week, etc). You can view the current epoch duration directly from the [PassportScores contract](https://etherscan.io/address/0x548ab653a6ab2e54debf05f3a728b602ac1c2e69).
* ****[**Merkle root**](https://www.investopedia.com/terms/m/merkle-root-cryptocurrency.asp)**:** Is the combined hash of all the elements in the tree. Each epoch progressively has different Merkle roots as new scores and addresses are indexed. You can verify a score's validity on-chain by providing a Merkle proof to the PassportScores contract.&#x20;
* **Merkle proof**: An array of hashes that can be combined with Merkle leaf to verify if this leaf is in the Merkle tree. The Merkle proof is the path from Merkle root to the Merkle leaf. If you hash the Merkle leaf with its corresponding Merkle proof and obtain the same root and the one saved on-chain, then this leaf is cryptographically verified.
* **Merkle leaf: **An object that is hashed and saved on the blockchain. In the context of the ARCx ecosystem, each Merkle leaf has the following format:

```
{
    "account": "0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E",
    "protocol": "0x617263782e6c6f79616c74790000000000000000000000000000000000000000",
    "score": "175",
}
```

| Property   | Description                                                                                                                                                                                  |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `account`  | The address associated with this score. There can be many different scores for the same address, but each score-address combination will be unique.                                          |
| `protocol` | The byte32 encoded representation of the protocol name. This is enforced for Smart Contract memory efficiency. The `protocol` in this example is the byte32 encoded value of `arcx.loyalty`. |
| `score`    | The quantification of each score. This must be a positive value, but can be any number within the scope of a [BigNumber](https://docs.ethers.io/v5/api/utils/bignumber/).                    |

### Verifying a Score&#x20;

To verify a score, simply get the score that you want to prove from the [API](verifying-passports.md#get-reputation-address-score-merkle-proof). Then you can pass the response directly\* to the contract to verify it.

_\*Drop the `metadata` attribute if included_

Example:

* Address: `0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E`&#x20;
* Protocol: `arcx.loyalty`

Get tuple [from API:](verifying-passports.md#get-reputation-address-score-merkle-proof)&#x20;

```
https://api.arcx.money/reputation/0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E/arcx.creditScore
```

Result:

```
{
    "account": "0xcd78358fb5fC823b9e789605B7b4fDc1dEf14A1E",
    "score": "175",
    "protocol": "0x617263782e6c6f79616c74790000000000000000000000000000000000000000",
    "merkleProof": [
        "0x6b9...5d3",
        "0x221...f5e",
        "0xe66...ff5",
        ...
    ]
}
```

Then use the resulting tuple within your Solidity code (`v0.8.4` compatible).

Example:

```
pragma solidity ^0.8.4;

...


function init(address _passportScoresAddress) external onlyAdmin initializer {
    ...
    
    require(
        _passportScoresAddress.isContract(),
        "DefiPassport: passport scores address is not a contract"
    );
    
    passportScoresContract = ISapphirePassportScores(_passportScoresAddress);
    
    ...
}

modifier checkScoreProof(
    SapphireTypes.ScoreProof memory _scoreProof
) {
    // Optional: Enforce verification from the caller only
    require(
        _to == _scoreProof.account,
        "The proof must correspond to the receiver"
    );
    
    passportScoresContract.verify(_scoreProof); // <--- How to verify score
    _;
}

...

// Will fail if proof is invalid
function doSomethingThatNeedsAValidScore(
    SapphireTypes.ScoreProof _scoreProof
) checkScoreProof(_scoreProof) {
    // Some code to be executed if the score proof is valid
}

// Will fail if proof is invalid, allows transaction preview to show revert
function verifyScore(SapphireTypes.ScoreProof calldata _scoreProof) external view returns(bool) {
    return passportScoresContract.verify(_scoreProof); 
}


```

You can find all types in our contracts [npm package](https://www.npmjs.com/package/@arcxgame/contracts).

### Help

If you have any questions or suggestions, we'd love your input on our [discord server](https://discord.com/invite/skwz6je).\
\
Happy building! ノ
