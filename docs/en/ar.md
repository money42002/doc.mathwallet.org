# Arweave

## Integrating

### Detecting the Provider

MathWallet will inject an object called `arweaveWallet` on the [window](https://developer.mozilla.org/en-US/docs/Web/API/Window) object of any web application the user visits.

To detect if a browser extension using this API is installed, you can check for the existence of the `arweaveWallet` object.

To make it easy to detect MathWallet specifically, the extension adds an additional walletName == `isMathWallet`.

![ar](https://mathwallet.oss-cn-hangzhou.aliyuncs.com/blog/upload/WechatIMG59.png)

If MathWallet is not installed, we recommend you redirect your users to [our website](https://mathwallet.org/). 

### ArConnect Compatibility

MathWallet Arweave wallet is compatible the ArConnect API which support dapp connect / disconnect / sign transaction etc.

Details:

[https://github.com/th8ta/ArConnect](https://github.com/th8ta/ArConnect)
