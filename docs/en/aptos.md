# APTOS

## Integrating

### Detecting the Provider

MathWallet will inject an object called `aptos` on the [window](https://developer.mozilla.org/en-US/docs/Web/API/Window) object of any web application the user visits.

To detect if a browser extension using this API is installed, you can check for the existence of the `aptos` object.

To make it easy to detect MathWallet specifically, the extension adds an additional `isMathWallet` flag.


```javascript
const isMathWalletInstalled = window.aptos && window.aptos.isMathWallet
```

If MathWallet is not installed, we recommend you redirect your users to [our website](https://mathwallet.org/). Altogether, this may look like the following.

```javascript
const getProvider = () => {
  if ("aptos" in window) {
    const provider = window.aptos;
    if (provider.isMathWallet) {
      return provider;
    }
  }
  window.open("https://mathwallet.org/", "_blank");
};
```

## More Resources

### Aptos Dapp Developer Guide

[https://aptos.dev/tutorials/your-first-dapp](https://aptos.dev/tutorials/your-first-dapp)

