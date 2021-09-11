# ETH DAPP Development Document

## Web dApp Development (Inside Wallet)

### Web3 API

Math Wallet is compatible with web3 API same as metamask.

#### Web3 API official document

[https://github.com/ethereum/wiki/wiki/JavaScript-API](https://github.com/ethereum/wiki/wiki/JavaScript-API)

#### Web3 API Demo Projects

Math Wallet web3 API development and testing sample

[https://github.com/mathwallet/math-ethjs](https://github.com/mathwallet/math-ethjs)



## Native dApp Development

### SimpleWallet API

If your DAPP is based on native development or browser based, you could open MathWallet to sign your transaction through SimpleWallet protocol or use Math Wallet to scan and authorize.

MathWallet SimpleWallet Protocol supports:

Native APP can open MathWallet to sign your transaction.

To use this API, please read the API doc:

[https://github.com/mathwallet/SimpleWallet](https://github.com/mathwallet/SimpleWallet)



#### SimpleWallet API Demo Projects

SDK example developed by Math Wallet team:

iOS – [https://github.com/mathwallet/MathWalletSDK-iOS](https://github.com/mathwallet/MathWalletSDK-iOS)

Android – [https://github.com/mathwallet/MathWalletSDK-Android](https://github.com/mathwallet/MathWalletSDK-Android)

Demo - [https://blog.mathwallet.org/?p=3372](https://blog.mathwallet.org/?p=3372)


### WalletConnect Protocol (QR code & Inside Mobile Browser)

WalletConnect is an open protocol for connecting desktop Dapps to mobile Wallets using end-to-end encryption by scanning a QR code.

Document:
[https://walletconnect.org/](https://walletconnect.org/)

Demo: [https://blog.mathwallet.org/?p=3361](https://blog.mathwallet.org/?p=3361)


### Q. How to know whether the address is opened by the dapp browser of Math Wallet ?

There are 2 ways:

1 Lookup Http Header:

If there’s “MathWallet” in User-Agent in HTTP Header, then it is visited by the browser of Math Wallet. (User-Agent: MathWallet)

2 Lookup injected js:

For ETH(BSC/Heco/Polygon and other EVM based), check ethereum.isMathWallet = true

![eth](http://qiniu.eth.fm/2021-07-28-eth.png)
