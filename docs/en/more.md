# More Q&A

### Q. How to know whether the address is opened by the dapp browser of Math Wallet ?

There are 2 ways:

1 Lookup Http Header:

If there’s “MathWallet” in User-Agent in HTTP Header, then it is visited by the browser of Math Wallet. (User-Agent: MathWallet)

2 Lookup injected js:

For ETH(BSC/Heco/Polygon and other EVM based), check ethereum.isMathWallet = true

![eth](http://qiniu.eth.fm/2021-07-28-eth.png)

For Polkadot(Kusama/Statemine and other substrate based), check injectedWeb3.mathwallet

![dot](http://qiniu.eth.fm/2021-07-28-dot.png)

For Solana, check solana.isMathWallet = true

![solana](http://qiniu.eth.fm/2021-07-28-solana.png)

### Q. How to get more current wallet information, such as orientation / language / fullscreen, etc?

We will need math-js-sdk: [https://github.com/mathwallet/math-js-sdk](https://github.com/mathwallet/math-js-sdk)

### Q. How to debug a dApp within Math Wallet?

Please read: [http://blog.mathwallet.org/?p=154](http://blog.mathwallet.org/?p=154)

### Q. Does Math Wallet support testnet chain environment and account?

Yes. You will need MathWallet5 and add testnet yourself.

### Q. How to open a dApp in landscape screen orientation?

There are 2 ways:

1 Math Wallet team can help you config your dApp opened in landscape mode by default, you just need to inform us.

2 You can use math-js-sdk: [https://github.com/mathwallet/math-js-sdk](https://github.com/mathwallet/math-js-sdk), issue the orientation() function.

### Q. How to open a dApp in full screen mode?

You can use math-js-sdk: [https://github.com/mathwallet/math-js-sdk](https://github.com/mathwallet/math-js-sdk), issue the fullScreen(1) function.
And we suggest you add a 'Close' button in your dApp, which need to issue fullScreen(0) or close() function.


### Q. How to get the current language in the dApp?

Sample code below:

```
/**
 * @return {string} country code: cn / ko / en
 */
var getNavLanguage = function(){
  navLanguage = (navigator.language || navigator.browserLanguage ).toLowerCase();
  switch(navLanguage)
  {
  case 'zh-cn' || 'zh-tw' || 'zh-hk':
    navLanguage = 'cn';
    break;
  case 'ko':
    navLanguage = 'ko'
    break;
  default:
    navLanguage = 'en';
  }
  return navLanguage;
}
```

### Q. Does MathWallet support DeepLink?


Yes. Sample:

[https://blog.mathwallet.org/?p=3389](https://blog.mathwallet.org/?p=3389)
