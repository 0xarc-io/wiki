# Context and challenges

### Requirements of the DeFi Credit Score

To deliver the DeFi Credit Score, the infrastructure needs to:

* Ingest and store transaction data from the blockchain
* Perform heavy calculations to derive a unique Credit Score for each wallet address
* Continuously ingest new transaction data and frequently update the Credit Score
* Allow us to modify the Credit Score parameters as required by an in-house risk function
* Publish all Credit Scores on-chain in a gas-efficient and secure manner
* Be verifiable on-chain to prevent fraud or exploitation
* Allow for external validation and verification to ensure Credit Scores are correct
* Scale publishing process to allow the indexing of many wallet addresses

### Challenges to overcome

The ARCx infrastructure was developed to overcome key data engineering challenges applicable to a range of use cases in crypto (not just the DeFi Credit Score). The following section briefly explains the challenges applicable to powering an on-chain Credit Score and other on-chain or off-chain use cases.

**(1) Data collection**

Ethereum and other major blockchains process millions of transactions each and every day. With terabytes of history and the need to ingest and enrich new data continuously, the cost and knowledge required to understand both current state and historical states of the blockchain is extremely high. To do this effectively, we needed to develop sophisticated data engineering pipelines and invest heavily in cloud storage and computing resources. So although blockchain transactions are widely accessible through the public ledgers, having a comprehensive and continuously updating dataset is most likely out of reach for most projects.

**(2) Data interpretation**

Individuals and their on-chain activity are represented as hexadecimal numbers known as “addresses” and “transaction hashes” respectively. Behind each transaction, an address (or user) is simply trying to achieve some objective, whether that’s swapping, staking, borrowing, voting, or any other arbitrary action facilitated by smart contracts. The challenge lies in understanding the context of such transactions and creating insights to craft meaningful wallet-level attributes that support a business objective. For the purposes of the DeFi Credit Score, the challenge is in understanding what factors demonstrate responsible borrowing behavior. This unlocks the ability to offer better capital efficiency in DeFi, thus creating a strong point of differentiation and driving business success metrics (e.g. loan book size).

Moreover, these unique custom attributes are not sufficient as stand-alone data points (e.g. “holds X tokens” or “has staked Y”). There is a second layer of computation required for understandable interpretation of multiple variables (e.g. “has done X, but not Y, and holds unrealized losses with Z token”). For this to be effective, we need to run advanced calculations across all wallet addresses on a continuous basis, updating our calculations and tweaking our formulas as new data comes in.

**(3) Data use**

Armed with continuously updating attributes for each wallet address, we can proceed in applying them towards a business objective. For ARCx Credit, this meant allowing our liquidity market to use the latest Credit Score of a given wallet address, verify it on-chain, and unlock borrower-specific offers in real-time (i.e. personalized max-LTV offer).
