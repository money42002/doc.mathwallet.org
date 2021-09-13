# Solana DAPP Development Document

# Detecting the Provider

MathWallet will inject an object called`solana` on the [window](https://developer.mozilla.org/en-US/docs/Web/API/Window) object of any web application the user visits.

To detect if a browser extension using this API is installed, you can check for the existence of the `solana` object.

To make it easy to detect MathWallet specifically, the extension adds an additional `isMathWallet` flag.

![solana](http://qiniu.eth.fm/2021-07-28-solana.png)

```javascript
const isMathWalletInstalled = window.solana && window.solana.isMathWallet
```

If MathWallet is not installed, we recommend you redirect your users to [our website](https://mathwallet.org/). Altogether, this may look like the following.

```javascript
const getProvider = () => {
  if ("solana" in window) {
    const provider = window.solana;
    if (provider.isMathWallet) {
      return provider;
    }
  }
  window.open("https://mathwallet.org/", "_blank");
};
```




## Web dApp Development

### RPC document

[https://docs.solana.com/](https://docs.solana.com/)

### Wallet Adapter API (lib for communicate with web wallet or extension)

[https://github.com/project-serum/sol-wallet-adapter](https://github.com/project-serum/sol-wallet-adapter)

### Web3 JS (create transactions in frontend)

[https://github.com/solana-labs/solana-web3.js](https://github.com/solana-labs/solana-web3.js)

### Connect to Wallet UI samples

[https://github.com/project-serum/serum-dex-ui](https://github.com/project-serum/serum-dex-ui)

[https://github.com/project-serum/oyster-swap](https://github.com/project-serum/oyster-swap)



### Add MathWallet Related Config

Changes Sample (if you are not using the latest sol-wallet-adapter and ui code)

[https://github.com/project-serum/oyster-swap/blob/master/src/wallet-adapters/math/index.tsx](https://github.com/project-serum/oyster-swap/blob/master/src/wallet-adapters/math/index.tsx)

[https://github.com/project-serum/oyster-swap/blob/master/src/context/wallet.tsx](https://github.com/project-serum/oyster-swap/blob/master/src/context/wallet.tsx)

[https://github.com/project-serum/serum-dex-ui/pull/63/files](https://github.com/project-serum/serum-dex-ui/pull/63/files)

Common errors in wallet.tsx config (which will cause the wallet cannot inject to the dapp site)

![mathso](http://qiniu.eth.fm/2021-09-01-mathsol1.jpg)

![mathso](http://qiniu.eth.fm/2021-09-01-mathsol2.jpg)




