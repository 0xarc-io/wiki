# ARCx Token

### Purpose of the Token

The core function of the ARCx Governance Token is to be the governance mechanism for the ARCx protocol itself. The token is intended to align incentives between various stakeholders within the ecosystem to promote sustainable growth and fair governance.

The ARCx Governance Token currently allows token holders to vote on expenditure from the treasury. In the future, ARCx token holders will be able to vote to receive cash flows generated from the network and participate in native on-chain governance to upgrade the protocol itself.

For more information on voting, please visit the page on [Governance](proposals-and-voting.md)

### Tokenomics

[AIP4](https://forum.arcx.money/t/aip4-simplifying-and-improving-the-arcx-tokenomics/120) passed on the [3rd September 2021](https://snapshot.org/#/arcx.eth/proposal/QmNgKXxL8GosVEc8bfniXPMzMSF5bNVatW5smmazsf4UJ8) involving a one-off mint of approximately 60 million ARCX to get the total supply to 100 million tokens. From here a new schedule was formed for the Angel investors, ARCx Team and $KERMAN holders (detailed below) with various unlock dates and a stream started where relevant. The initial unlock dates were pushed back to flatten the inflation curve. The below chart shows the release of ARCX tokens over time.

![](<../.gitbook/assets/Untitled (22).png>)

### Token Distribution Breakdown

The below pie charts show how the different allocations change at two instances in time. Each chart shows the total **locked** allocation and its change to becoming unlocked (circulating).

![](<../.gitbook/assets/Untitled (23) (1).png>)

**Note:** There are still some ARCX OLD tokens (around 600 at the time of writing) that are yet to be migrated across. This will add to the circulating supply as and when they migrate. There is no time cap on this, the [migration portal](https://migration.arcx.money/) will remain open indefinitely.

![](<../.gitbook/assets/Untitled (24) (1).png>)

**Update:** Following the passing of [AIP5](https://forum.arcx.money/t/aip5-boosting-arcx-liquidity/135), over 5 million ARCX from the treasury was added to the Uniswap v3 position. This has resulted in an increase of 5% to the circulating supply.

### Token Split and Migration

After a successful snapshot vote on [AIP-2](https://arcx.substack.com/p/aip-2-arcx-token-split-110000) - the ARCx community has proceeded with a split of the ‘Old ARCx Governance Token’ 1:10,000. This will result in a total supply of 100,000,000 ARCx Governance Tokens.

As an indication, if you hold 1 ARCx worth $10,000 pre-split, you would get 10,000 ARCx post split - each worth $1.00.

The migration contract is accessible through the arcx.money website, which will allow Old ARCx token holders to burn their old tokens and mint new ARCx tokens. This contract will run in perpetuity, meaning that there is no risk of a holder missing out on the migration.

The original ARCx Governance Token will be called the ‘Old ARCx Governance Token’ and the new token post-split will simply be referred to as the ARCx Governance Token.&#x20;

The core function of the ‘post-split’ ARCx Token will be exactly the same - to govern the protocol, and to use it as a tool to incentivize growth and integrations with other protocols.

You can [migrate your tokens here](https://migration.arcx.money/).

### Token technicals

Listed below are all the addresses related to the ARCx token.

| **Address**                                                                                                                                                                                         | **Description**                                                                                                                                                                                     |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><a href="https://etherscan.io/address/0x1321f1f1aa541a56c31682c57b80ecfccd9bb288#code"><strong>0x1321f1f1aa541a56c31682c57b80ecfccd9bb288</strong></a><strong></strong><br><strong></strong></p> | **Official ARCx Governance Token Address.** Minting capabilities controlled by the ARCx team                                                                                                        |
| [**0xed30dd7e50edf3581ad970efc5d9379ce2614adb**](https://etherscan.io/address/0xed30dd7e50edf3581ad970efc5d9379ce2614adb)                                                                           | **(Old) ARCx Governance Token** before 10,000:1 split authorized by Arcx Improvement Proposal-2 (AIP-2)                                                                                             |
| [**0x1debbc50322150eb44de3b663d5faa89c12b07ff**](https://etherscan.io/address/0x1debbc50322150eb44de3b663d5faa89c12b07ff)                                                                           | **ARCx Emissions Distributor.** 19.1% of the supply goes to the community treasury, 15.5% to the core team & 5.41% to the original angel round**.**                                                 |
| [**0xafa06707a4c859722480b35822620d2eb14af59e**](https://etherscan.io/address/0xafa06707a4c859722480b35822620d2eb14af59e)                                                                           | **Vested Phase 2 tokens** that will be distributed 6 months after the launch of the token.                                                                                                          |
| [**0xa53ab7f36c147b4bfca3c9c236de660f30a9d948**](https://etherscan.io/address/0xa53ab7f36c147b4bfca3c9c236de660f30a9d948)                                                                           | **Unsold Phase 2 tokens** that can be sold at the discretion of the ARCx team.                                                                                                                      |
| [**0x4317D259fCCe32ebbB508C27b12F4AfACA074AE3**](https://etherscan.io/address/0x4317D259fCCe32ebbB508C27b12F4AfACA074AE3)                                                                           | **ARCx DAO Treasury Address.** Funds are voted on via Snapshot voting and executed via a multi-sig.                                                                                                 |
| [**0x88CDF983117505Fee6433277D14C298ECfBEeAd6**](https://etherscan.io/address/0x88CDF983117505Fee6433277D14C298ECfBEeAd6)                                                                           | **Vested Core team tokens.** Initial lock up for 6+6 months, vested continuously for 36 months after. Total 4 year vesting. 15.5% total, 1% allocated to $KERMAN holders (see below)                |
| [**0x75Aa7a55df3BD077c3238a5eB9722290a4c8A3C0**](https://etherscan.io/address/0x75Aa7a55df3BD077c3238a5eB9722290a4c8A3C0)                                                                           | **Vested Angel round tokens.** Initial lock up for 6+6 months, earned continuously via emissions for a total of 4 years.                                                                            |
| [**0xBaDADFcac026820Af874b9ed52d4D19435b6cf0B**](https://etherscan.io/address/0xBaDADFcac026820Af874b9ed52d4D19435b6cf0B)                                                                           | **Additional  Core team (social token) allocation.** 1% (from the Core team 15.5%) is distributed to $KERMAN holders. More details around claiming for this will be made in the coming months.      |
| ****[**0x2Db5553872382De018efD3eB36B7e077dBf3b8f3**](https://etherscan.io/address/0x2Db5553872382De018efD3eB36B7e077dBf3b8f3)****                                                                   | **ARCx Growth Allocation Address.** Treasury allocation managed by the Llama team. [Details here.](https://forum.arcx.money/t/introducing-arcx-growth-allocation-i-deploy-treasury-productively/61) |

**Note:** 6+6 months refers to 6-months pre-token tradability and 6-months post-token tradability. This was a decision taken by the Core team and Angel investors to ensure that the token tradability event was as fair as possible to network participants.

