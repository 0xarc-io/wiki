# Managing a position

### Connect your wallet to the Polygon Network

ARCx Credit operates on the Polygon Network, a scaling solution for Ethereum. Before interacting with the application, you will need to connect and use your Web3 wallet on the Polygon Network. We recommend using [Metamask wallet](notion://www.notion.so/products/set-up-metamask) as your Web3 wallet, though we support any wallet compatible with [Wallet Connect](https://walletconnect.com/).

* Log in to your wallet
* Go to[https://chainlist.org/](https://chainlist.org/) site
* In the search box insert _**polygon mainnet**_
* Click the _**connect your wallet**_ button on the top right
* Click _**add to Metamask**_ button

### Connect your wallet to ARCx Credit

Visit [https://arcx.money](https://arcx.money) and click “connect wallet” on the top right corner. This will open up a prompt to select either Metamask or Wallet Connect. Clicking on either option will prompt your wallet to connect to the website. Once connected, the “connect wallet” button will be replaced by your connected wallet address. If you wish to disconnect your current wallet, you can do so by clicking on this button and selecting “disconnect”.

![Wallet connect from the arcx.money landing page](<../../.gitbook/assets/Wallet connection.png>)

### Select a vault

Once you have connected your wallet, head over to the Borrow Vaults section of the app and select a vault for the collateral you would like to use. Note, we offer three vaults for each collateral type, with each distinguished by the level of capital efficiency you can unlock.

![Borrow Home Page (highlighting the Vault Selector)](<../../.gitbook/assets/Borrow home page.png>)

Vaults with higher capital efficiency (i.e. higher maximum LTV) can be unlocked as you build your DeFi Credit Score.&#x20;

For more information, see [vault design and credit limits](vault-design-and-credit-limits.md).

### Deposit collateral

You will now find yourself on the vault action page. To deposit collateral, (1) select “deposit” from the action selector dropdown; (2) select the amount of collateral you would like to deposit (or hit the “max” button); and (3) click deposit. Note, the first time you do this, you will need to approve the use of your collateral by signing a transaction with your Web3 wallet.

![Vault Action Page (highlighting input fields and transaction initiation button)](<../../.gitbook/assets/Vault action page.png>)

### Borrow stablecoins

Once you have collateral deposited into a vault, you will then be able to start borrowing.

As shown in the screenshot below, to do this, (1) select “borrow” from the action selector dropdown; (2) select the amount you wish to borrow (or hit either the “optimize” or “max” buttons); and (3) click borrow. The “optimize” button calculates and pre-fills the amount you should borrow or repay in order to maximize the growth of your DeFi Credit Score.

![Vault Action Page (highlighting input fields and transaction initiation button)](<../../.gitbook/assets/Vault action page 2.png>)

Below the input field, you will notice the transaction impact values changing. As shown in the screenshot below, under (1), you will find your anticipated borrow usage alongside an explanation of how the transaction will impact the growth of your DeFi Credit Score going forward. Under (2), you will find the impact of the transaction on your vault position, including deposited collateral, borrowed amount, available credit, and collateral liquidation price.

Note, "available credit" is based on either the deposited collateral and maximum LTV, or the vault-specific credit limit (whichever is lower).&#x20;

![Vault Action Page (highlighting vault-level position information)](<../../.gitbook/assets/Vault action page 3.png>)

### View your positions

With one or more active vaults, you can view the status of your positions from the Borrow Home Page. Under (1), you will find your overall position summary across all active vaults. This section shows your borrow usage, as well as the amount borrowed, deposited and interest rate being charged. There is a graphical representation of borrow usage, how this ties back to the speed at which your DeFi Credit Score grows, and a suggestion on how to improve your position. Under (2), you will find the borrow usage of your active vaults shown on the right-hand side.

![Borrow Home Page (highlighting the Position Summary card and Vault section)](<../../.gitbook/assets/Borrow home page 2.png>)

To view detailed information at an individual vault-level, simply return to the vault action page. From here, you will find your vault-level borrow usage, a recommendation for what to do to optimally grow your DeFi Credit Score, and other basic position information.

![Vault Action Page (highlighting vault-level position information)](<../../.gitbook/assets/Vault action page 4.png>)

### Avoid liquidation

Liquidation events will negatively impact your DeFi Credit Score. To avoid liquidations, it is important that you monitor the market and actively de-risk your borrowing positions during periods of high volatility. Should any of your active positions exceed 90% borrow usage, a warning message will appear on the Borrow Home Page, as shown below next to (1) and (2), to alert you to either repay your loan or add additional collateral.

![Borrow Home Page (highlighting the liquidation warning message)](<../../.gitbook/assets/Borrow home page 3.png>)

### Manage your positions

With an active vault, you can easily manage your positions by returning to the Vault Action Page. The process for repaying and withdrawing is the same as for depositing and borrowing. Simply change the action selector dropdown, input your amounts and click the primary button at the bottom to initiate the transaction

### Exiting your position

To completely exit a vault, you will need to repay all of your debt and then withdraw all of your collateral. To do this, you can simply click the “max” button beside the input field to ensure everything is repaid and withdrawn from the vault. If you follow these steps, the transaction initiation button will read “Exit”, and this will completely empty the vault of your collateral.

![Vault Action Page (showing an exit transaction)](<../../.gitbook/assets/Vault action page 5.png>)
