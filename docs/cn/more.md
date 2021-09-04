# 更多问题

### Q 如何判断是否为MathWallet的DApp浏览器环境？

一般有两种方式

1 查询 HTTP Header 的 User-Agent

HTTP Header 的 User-Agent 里面如果有 “MathWallet”，表示是麦子钱包的浏览器访问 (User-Agent: MathWallet)

2 查询注入的 JS

以太坊系 ETH(BSC/Heco/Polygon 以及其它基于 EVM 的链), 检查 ethereum.isMathWallet = true

![eth](http://qiniu.eth.fm/2021-07-28-eth.png)

波卡系 Polkadot(Kusama/Statemine 以及其它基于 substrate 的链), 检查 injectedWeb3.mathwallet

![dot](http://qiniu.eth.fm/2021-07-28-dot.png)

Solana 链, 检查 solana.isMathWallet = true

![solana](http://qiniu.eth.fm/2021-07-28-solana.png)

### Q: 如何在 DAPP 页面获取钱包信息、全屏、打开微信、横屏、当前语言等信息和操作？

可以通过 math-js-sdk: [https://github.com/mathwallet/math-js-sdk](https://github.com/mathwallet/math-js-sdk)

### Q: 如何在麦子钱包中调试 DAPP？

麦子钱包提供DAPP浏览器和手机端调试工具，具体调试方法查看：[http://blog.mathwallet.net/?p=1248](http://blog.mathwallet.net/?p=1248)

### Q: 如何在麦子钱包是否支持测试链？

支持，需要下载MathWallet5版本，并自定义网络

### Q：如何让 DAPP 在麦子钱包中【横屏】打开？

有两种方法：

1 由麦子钱包配置该 DAPP 横屏打开，只需要联系麦子钱包团队即可

2 在 DAPP 页面上调用 math-js-sdk: [https://github.com/mathwallet/math-js-sdk](https://github.com/mathwallet/math-js-sdk) 的 orientation 方法

### Q: 如何让 DAPP 在麦子钱包中【全屏】打开？

在 DAPP 页面上调用 math-js-sdk: [https://github.com/mathwallet/math-js-sdk](https://github.com/mathwallet/math-js-sdk) 的 fullScreen(1) 方法。
同时建议您在 DAPP 上加入退出全屏或退出按钮，并调用 math-js-sdk 的 fullScreen(0) 和 close() 方法。

### Q: 如何通过钱包接口获取用户手机的 Device ID？

在 DAPP 页面上调用 math-js-sdk: [https://github.com/mathwallet/math-js-sdk](https://github.com/mathwallet/math-js-sdk) 的 getAppInfo() 方法，在返回值中获取 deviceId 即可。

### Q: DAPP 怎样获取钱包DAPP浏览器语言？

示例代码如下：

```
/**
 * 获取浏览器语言类型
 * @return {string} 浏览器国家语言
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


### Q: 如何通过Deeplink打开麦子钱包，跳转到 DAPP 页面，完成操作后回调？

你可以使用 Deeplink，示例URL代码如下

https://blog.mathwallet.org/?p=3389
