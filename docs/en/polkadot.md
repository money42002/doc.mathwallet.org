# Polkadot DAPP Development Document

## Web dApp Development

### PolkadotWeb3JS API

[https://polkadot.js.org/](https://polkadot.js.org/)

Sample (Sign Transactions)

[https://github.com/mathwallet/math-substratejs](https://github.com/mathwallet/math-substratejs)

### Q. How to know whether the address is opened by the dapp browser of Math Wallet ?

There are 2 ways:

1 Lookup Http Header:

If there’s “MathWallet” in User-Agent in HTTP Header, then it is visited by the browser of Math Wallet. (User-Agent: MathWallet)

2 Lookup injected js:

For Polkadot(Kusama/Statemine and other substrate based), check injectedWeb3.mathwallet

![dot](http://qiniu.eth.fm/2021-07-28-dot.png)
