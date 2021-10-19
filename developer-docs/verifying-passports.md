---
description: A brief guide on accessing our different
---

# API

### Introduction

When a user receives a DeFi Passport, you can be assured that they've passed some basic criteria around activity for their wallet. For example, the current criteria ensures that they have:&#x20;

* 30 Days of wallet history
* Interacted with more than 5 unique address
* Spent at least 0.01 ETH on gas
* Paid or staked tokens for a DeFi Passport

This can be valuable if you're a developer and want some basic assurances around the user you're allowing to interact with your dApp. Below are the two methods you can use to check if a user holds a valid DeFi Passport.

### On-Chain

If you'd like to check if a user has DeFi Passport directly on-chain here are the steps you need to take:

1. Call `tokenOfOwnerByIndex(address, 0)` on the DeFi Passport ERC721 contract ([0x933492b6B7038A7e4f14b64DEFe40463F9bc3508](https://etherscan.io/address/0x933492b6B7038A7e4f14b64DEFe40463F9bc3508)), where`address` is the address you'd like to check has a valid passport
2. **That's it.** If the user has a valid passport you'll get the ERC721 token id of their DeFi Passport. A single address cannot have more than one DeFi Passport so the token id you receive is guaranteed to be unique.

We've designed the passport to be highly interoperable within DeFi and we hope you find it easy to integrate with as well.

### API

In the case that you'd like to check if a user has a DeFi Passport via a REST API that's just as simple. Simply call the following endpoint where `address` is the address of the user to check.

`GET`: `https://api.arcx.money/passports/{address}`

Here's an example response for the address [0xFEC18996C36D02902E4c55bcFB7A1c73AA1500Cd](https://api.arcx.money/passports/0xFEC18996C36D02902E4c55bcFB7A1c73AA1500Cd):

```
{
  "address": "0xFEC18996C36D02902E4c55bcFB7A1c73AA1500Cd",
  "status": "active",
  "dateIssued": 1629501686,
  "tokenId": 6,
  "imageUrlFront": "https://api.arcx.money/passports/image/6",
  "imageUrlBack": "https://api.arcx.money/passports/image/6?side=back&glow=true",
  "videoUrl": "https://api.arcx.money/passports/video/6",
  "animation_url": "https://api.arcx.money/passports/video/6",
  "activeSkin": {
    "title": "ARCx Default White",
    "description": "ARCx Default DeFi Passport Skins. Comes in black, purple and white.",
    "tokenIds": ["3"],
    "contract": "0x302434B8676048b9FDE0aD20952999C84c7f1428",
    "group": "arcx",
    "name": "white",
    "imageUrl": "https://api.arcx.money/skins/image/arcx/3",
    "videoUrl": "https://api.arcx.money/skins/video/arcx/3"
  }
}
```

We hope you find this useful as an integration guide of how to incorporate the DeFi Passport into your dApp.&#x20;

**If you have any questions please don't hestitate to drop into our Discord to ask any questions!**

****
