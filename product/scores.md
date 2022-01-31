# 💯 Scores

### What are scores?

Scores are numerical values assigned to a specific wallet address that are derived from wallet activity, and which are continuously published on-chain. Scores can be used to understand historical behaviour in the context of specific “games” played across DeFi. For instance, a credit score which evaluates the credit-worthiness of individuals based on their past and ongoing borrowing behaviour, or a loyalty score to evaluate the affinity of a user to a particular protocol.

The scoring system consists of a service that continuously ingests and processes raw on-chain data for every wallet address, and then publishes that data on-chain via a Merkle root. Given that scores are published on-chain, we are able to interact with them through smart contracts for use in other DeFi applications. One use case of the Credit Score is to give borrowers the ability to access personalised and preferential c-ratio and borrow limits (among other benefits) via a CDP-based borrowing service.

### How scores work

The ARCx passport contains a variety of scores across different systems which are updated every epoch. These scores are saved in a Merkle Tree, and any participant with an active passport can verify any score against the equivalent Merkle Root which is published on-chain.

### ARCx Loyalty Score

The ARCx Loyalty Score measures a Passport Holder's participation and engagement across yield farming, token staking and protocol governance within the ARCx ecosystem dating back to September 2020. Below are a list of the rules that impact your Score:

| Score Rules                                         | Score impact         |
| --------------------------------------------------- | -------------------- |
| User participated in any previous ARCx yield farm   | + 50 Points per farm |
| User stakes ARCx tokens for stARCx                  | + 50 Points          |
| User migrated ARCx tokens from old contract address | + 50 Points          |
| User voted in an ARCx Snapshot proposal             | + 50 Points per vote |
