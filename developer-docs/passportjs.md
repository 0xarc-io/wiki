---
description: Display the ARCx DeFi Passport in your dApp.
---

# 🎨 Passport.js

### Introduction

`Passport.js`  is a small `React.js` component which displays a wallet's DeFi passport.&#x20;

![Live demo ](../.gitbook/assets/passportjs.gif)

### Install

`Passport.js` is available with both  `yarn` and `npm`.

```
npm install @arcxmoney/passport-js --save
```

```
yarn add @arcxmoney/passport-js 
```

### Basic Usage

Once installed, import the `Passport` component and use it anywhere in your application.&#x20;

Here is a basic example using the `useWeb3React` hook with the `Passport` component

```
import { Passport } from '@arcxmoney/passport-js';
import { useWeb3React } from '@web3-react/core'

const Page = () => {
    const { account } = useWeb3React();
    return (
        <Layout>
            <Passport account={account} />
        </Layout>
    );
}
```

### Additional Parameters

The only required parameter is `account`, all other properties are optional. Default values can be seen below:

```
<Passport
    account= '0x123...123', //REQUIRED
    width = 256,
    height = 256,
    position = 'fixed',
    chainId = '1',
    arcxUrl = 'https://api.arcx.money', 
    closable = true,
    showSpinner = false,
    analytics = true,
/>
```

#### Passport Properties

<table><thead><tr><th>Property</th><th data-type="select">Type</th><th>Description</th><th data-type="checkbox" data-hidden>Required?</th></tr></thead><tbody><tr><td><strong>account</strong></td><td></td><td>The associated address with a DeFi Passport. If an address does not have a DeFi Passport, the component will not display anything.</td><td>true</td></tr><tr><td><strong>width</strong></td><td></td><td>The width of the component.</td><td>false</td></tr><tr><td><strong>height</strong></td><td></td><td>The heigh of the component.</td><td>false</td></tr><tr><td><strong>position</strong></td><td></td><td><p>Behaviour of position:</p><ul><li><code>fixed</code> : Have the passport float in the lower right corner of the screen</li><li><code>flex</code> : Display the passport where the component is placed.</li></ul></td><td>false</td></tr><tr><td><strong>chainId</strong></td><td></td><td>Chain identifier of connected network.</td><td>false</td></tr><tr><td><strong>arcxUrl</strong></td><td></td><td>Endpoint to fetch passport metadata.</td><td>false</td></tr><tr><td><strong>closeable</strong></td><td></td><td>Allow the component to be dismissed.</td><td>false</td></tr><tr><td><strong>showSpinner</strong></td><td></td><td>Shows a loading animation (spinner) while the passport loads.</td><td>false</td></tr><tr><td><strong>analytics</strong></td><td></td><td>Participate in providing metrics to the ARCx engineering team. </td><td>false</td></tr></tbody></table>

### How it works

If an address has no DeFi passport, nothing shall be shown.

This package simply fetches an address' information from our [API](verifying-passports.md) and uses WebGL + CSS to wrap everything into a nice `React.js` component. It's a light-weight package to help with the integration of the DeFi Passport into any dApp which wants to integrate with us.



### Help

If you have any questions or suggestions, we'd love your input on our [discord server](https://discord.com/invite/skwz6je).\
\
Happy building! ノ



### Changelog

As seen in [npm registry](https://www.npmjs.com/package/@arcxmoney/passport-js).

#### \[1.0.3] - 2021-10-18

* Fixed issue with metrics tracking
* Changed arcxUrl default value to stable endpoint

#### \[1.0.2] - 2021-10-13

* Added WebGL properties
* Added cross-chain support

#### \[1.0.1] - 2021-10-13

* Fixed bug with the front image
* Removed score on the back-side
* Added ability to dismiss

#### \[1.0.0] - 2021-10-08

* Add package on NPM
