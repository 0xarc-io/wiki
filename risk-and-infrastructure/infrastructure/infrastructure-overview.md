# Infrastructure overview

### **Score creation**

The DeFi Credit Score is processed using custom data pipelines that pull on-chain data sources. Our pipelines are flexible, which allows us to increase the scope of data included in the Credit Score as required. The decision to use custom ETL pipelines allows our score designers to experiment with complex score logic with minimal effort (compared to endless SQL queries, for instance). Having a large, accessible and tailored dataset enables quick adjustments and in-depth analyses.

### **Score publishing**

The DeFi Credit Scores (and other on-chain scores) are combined into Merkle Trees, with its Merkle root (i.e. the root of all combined trees) being published on every blockchain we support. This process occurs every Epoch, which is currently set at a 24 hour window. To save on resources and processing time, subsets of scores are combined into smaller Merkle Trees, so as to be created in parallel. Then, the roots of each tree are combined into another Merkle Tree, and the process is repeated. The final Merkle Tree thus contains all the Credit Scores and are verifiable against the final Merkle Tree’s root deployed on each respective blockchain. All roots on each blockchain are equivalent at each epoch. This also means Credit Scores are chain agnostic (i.e. same score on each blockchain).

Before a new root becomes active on the blockchain, it must first spend 1 epoch on the \*[SapphirePassportScores\* contract](https://polygonscan.com/address/0xec73bB9Ce38aFE712A4b9a820bc34A2ddf50e990#readProxyContract) as the “upcoming Merkle root”. This intermediary step of having a public “upcoming root” provides an additional layer of security and transparency, allowing for anyone to externally validate both the “current root” and the “upcoming root”. When a new root is thus published, the “upcoming root” becomes the “current root”, and the new root takes its turn as the “upcoming root”. This also allows for integrity and security checks for an entire epoch before any root goes live. This entire process provides many failsafes while also providing a gas-efficient and cryptographically secure way to publish scores on-chain.

### **Score verification**

Applications wanting to use a score on-chain will need to fetch its proof, which can be found via our [publicly accessible REST API](https://docs.arcx.money). Third parties can verify any score on-chain by passing its proof to the `verify(...)` function on our [SapphirePassportScores contract](https://polygonscan.com/address/0xec73bB9Ce38aFE712A4b9a820bc34A2ddf50e990#readProxyContract).

### Comparison table

Alternative solutions to the problems described above exist, but these suffer from a variety of  challenges as described below:

| Option                                               | Pros                                                                                                                                                            | Cons                                                                                                                                         |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Merkle Root Publishing**                           | <ul><li>No external dependency</li><li>Gas efficient (single Merkle Root)</li><li>Low data integrity risk</li><li>Highly flexible</li><li>Transparent</li></ul> | <p></p><ul><li>Slower score updates</li><li>Large infrastructure to build</li></ul>                                                          |
| **Publish on-chain through existing oracle service** | <ul><li>No need to build extra infrastructure</li><li>Faster score updates</li></ul>                                                                            | <ul><li>Gas intensive</li><li>High data integrity risk</li><li>Not as transparent</li><li>Not flexible</li><li>External dependency</li></ul> |
| **Build competing oracle service**                   | <ul><li>No external dependency</li><li>Faster score updates</li></ul>                                                                                           | <ul><li>Gas intensive</li><li>High data integrity risk</li><li>Not as transparent</li><li>Immense infrastructure to build</li></ul>          |
