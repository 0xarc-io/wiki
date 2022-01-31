# ⚙ Integrations

If you are looking to partner with ARCx on an integration, please reach out via [Discord](https://discord.gg/arcx).

### Scores

Scores are numerical values assigned to a specific wallet address that are derived from wallet activity, and which are continuously published on-chain. We use a system called “Score Builder” to rapidly design and deploy scores on top of ARCx infrastructure at scale. Score rules (i.e. the on-chain events or attributes that count toward a specific Score) can be developed in consultation with ARCx.

We have developed a number of examples to show the flexibility of the system, including loyalty scores and credit scores. Since Scores are published on-chain, they can be used by other DeFi applications to achieve a variety of objectives, including identifying and rewarding loyal users with airdrops or whitelists, or incentivising governance participation through surfacing Snapshot voting behaviour on the Passport.

Score Builder can unlock new and interesting use cases that build community, protect value, create utility and make using decentralised finance more fun. If you’re interested in developing a Score with ARCx, please reach out to us via [Discord](https://discord.gg/arcx).

### Available chains

ARCx is currently available on Ethereum Mainnet, but we are working toward launching on Polygon by end of Q1 2022.

### Airdrops and whitelists

Our scoring infrastructure allows you to effectively filter the universe of wallet addresses to a subset of your choosing. One very strong use case for this is for determining the recipients of an Airdrop. In an [article published on our Substack](https://arcx.substack.com/p/understanding-the-ribbon-finance) in October 2021 where we evaluated the performance of the Ribbon Finance Airdrop, we found that Ribbon could have potentially saved between 1.23M and 8.12M RBN had they removed the opportunity sybil attack - something which could have been achieved by using a Score.

If you are interested in optimising an Airdrop or Whitelist, please reach out to us via [Discord](https://discord.gg/arcx).

### Engineering integrations

The ARCx team provides a variety of endpoints to 3rd-party developers to facilitate the acquisition of data related to ARCx products. Most of the information returned by our endpoints can also be parsed from on-chain logs. There are three main categories to our endpoints:

* Scores: The ARCx infrastructure creates on-chain scores for a variety of addresses. This data is used by 3rd party developers to make data-driven decisions on-chain. You'll find an account's profile and fetch proofs of particular scores using these endpoints.[.](https://www.notion.so/developer-docs/smart-contracts)
* Passports: The ARCx Passport is the key to the ARCx ecosystem. It enables staking, borrowing and skin features. This is a visual representation of your blockchain identity, but does not provide any benefit outside the ARCx ecosystem
* Protocols: ARCx has a variety of scores and partnerships with other dApps. These endpoints allow for transparency on who is integrated with ARCx and which scores are currently being indexed

More information can be found in the [Developers section](broken-reference) on Gitbook
