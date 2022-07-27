# Background

### Introduction

One of the most compelling use cases for on-chain reputation is a credit score that powers more efficient lending markets. The DeFi borrowing products of today treat all users the same, regardless of their risk profile. To preserve solvency in light of high volatility and low liquidity, Protocols impose high collateralization ratios (often \~150% on borrowing against ETH), which leads to inefficient capital allocations across the industry. But when we analyze historical data, we find that strict enforcement of these rules are unfavorable to most borrowers who exhibit risk averse borrowing behavior.

### Challenges

One of the fundamental characteristics of most blockchains is the concept of pseudo-anonymity, which refers to the fact that all actors in the system have their true identities obfuscated behind a unique address on the ledger. These identities are very cheap and easy to create, with the ability to create millions of new addresses for effectively zero cost. This liberating characteristic is also one of DeFi’s key limitations. It is assumed that since addresses are cheap, plentiful, and anonymous, it is effectively impossible to build reputation-based applications. Traditional financial products such as unsecured loans rely on the identity of the borrower being known. Risks associated with defaults and illiquidity on bad debts can often be mitigated through civil action on the individual, or a looming threat of their financial reputation being tarnished by their actions.

DeFi is unable to influence market participants in the same manner. An address that defaults on an undercollateralized loan can simply abandon its address - there is no way to seek damages, as the human identity of the address is impossible to know.

As a result of this pseudo-anonymity, protocols are forced to assume that all market participants are malicious and looking for ways to extract value from the protocol. This has led to very conservative risk parameters being set for protocols, with collateralization ratios often exceeding 150% for highly liquid and stable assets. Protocols too must levy a hefty percentage of interest collected by liquidity providers - typically a double-digit percentage of the exchange - in order to fill their war chests with enough capital to survive periods of high price volatility, congested networks, and illiquid assets.

### Design principles

The design of the DeFi Credit Score aims to balance the competing priorities of risk and user experience.

* From a risk perspective, it was essential that we maximize profitability and minimize toxic debt in our loan book. ARCx has invested heavily in building one of the most sophisticated risk management teams in crypto, and we are continually working to improve our risk parameters to optimize profitability. Having said that, what we found to be “optimal” from a risk perspective is often suboptimal for the user.
* From a user experience perspective, it was important that the DeFi Credit Score was explainable and fun. Earlier iterations of the DeFi Credit Score we developed were either too difficult to explain (with many rules and exceptions) or were unexplainable due to being “black box” calculations that simply returned a result without any explanation. Feedback during testing was overwhelming in favor of a system that could easily be explained and was fun to use.

***
