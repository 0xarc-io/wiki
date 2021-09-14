---
description: Display a user's DeFi Passport in your app
---

# Passport.js

### Introduction

Passport.js ノ is a small React library that offers interactive components to display an individual's DeFi passport in your application.

[Check out the demo here](https://passport-js-example.netlify.app/)

Here's a demo address you can use to test if an account has a DeFi Passport: \``0xE4FbF25Aa95363EFF2fF6459476763B34F7c190B`

### How it works

The `Passport` component fetches an address' information from our backend servers and upon success returns the user's passport video.

 If the user has no DeFi passport, no widget will be shown.

![Passport component](../.gitbook/assets/defi-passport.gif)

### Installation

Install our package either through `yarn` or `npm`

```text
npm install @arcxmoney/passport-js --save
```

### Implementation

The `Passport` component is an absolute positioned component written to load on top of your application. We recommend placing it higher up your component tree for readability, but also inside your Web3 provider.

Below is an example of how to combine the `useWeb3React` hook with the `Passport` component

```text
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

### Styling

The underlying `<video />` component is fully customizable through the `videoStyles` prop.

```text
<Passport
    videoStyles={{ border: '3px solid red' }}
    account={USER_ADDRESS} 
/>
```

#### Passport Properties

| Name | Description | Required? | Default Value |
| :--- | :--- | :---: | :---: |
| **account** | The user's address. | Yes |  |
| **analytics** | Voluntary prop to activate if you wish to help us out by sharing metrics. 🙂 | No | true |
| **videoStyles** | Customize styles for the  underlying video component. | No | Default Styles |

### Roadmap

We will be actively working on this library to help other protocols and builders integrate DeFi Passports and reputation.  
  
**Here's a small list of things currently being worked on** 

* [x] Interactive video component
* [ ] Utility functions for retrieving an account's passport information
* [ ] Fully interactive WebGL Passport component

If you have any questions or suggestions, feel free to raise an issue in our repository.  
  
Happy building! ノ

