# Core Concepts

### Minting

Minting is one of the ways you are able to create STABLEx. You effectively borrow STABLEx from the protocol whilst providing collateral. Once you have minted STABLEx you will be able to see in the Vaults \([https://app.arcx.money/vaults](https://app.arcx.money/vaults)\) how much collateral you have deposited as well as how much STABLEx you have minted

### Interest Rates

When you mint STABLEx you create a debt vault and will be required to pay interest. Interest accrues continuously and you will be able to see it in the front end

### Collateral Ratios

The collateral ratio is an important concept. It determines how much collateral you require in order to mint 1 STABLEx token. For example if you have a collateral ratio of 200% then in order to mint 1 STABLEx you must provide at least 2 yUSD. This is a very simple example and what you are able to mint may vary depending on the price of the underlying collateral

#### Minimum Collateral Ratio

After you have minted if you look at your vault you will see that there is a minimum collateral ratio. This is a very important number! Make sure that your collateral ratio is always **greater than** your minimum collateral ratio otherwise you may face potential liquidations

### Liquidations

A vault will be liquidated if the collateral ratio is less than the minimum collateral ratio required. When this occurs your vault will be closed and your collateral will be returned to you with a 2% liquidation penalty applied.

Please note that interest affects your collateral ratio so keep an eye on this!

#### Maintaining your Minimum Collateral Ratio

There are generally two ways to maintain this:

1. For a more passive method, put a buffer higher than whatever the minimum collateral ratio is such that your chance of liquidation is significantly lower. For example if it is at 200% you may put enough for it to be at 300%
2. For a more active method, continually monitor and then add additional collateral to the vault if it starts to dip below a threshold

### Savings Rates

A method to incentivise people to either mint or buy STABLEx is the savings rate. The savings rate is reflected as a percentage and shows how much you will earn when you stake your STABLEx into the savings contract. You can stake your STABLEx in the savings contract: [https://app.arcx.money/savings](https://app.arcx.money/savings)

Earnings are denominated in STABLEx - i.e. if you deposit 10,000 STABLEx with a 20% savings rate you should expect to earn 2000 STABLEx over the course of a year

### Closing Vaults

When you close your vault you effectively pay back your loan. By paying back STABLEx you receive all your collateral back.

The amount of STABLEx required to pay back your vault will be the amount you minted **plus** any interest that has accrued

