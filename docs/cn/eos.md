# EOS DAPP 开发文档

## H5 DAPP 开发

### Scatter API（推荐）

麦子钱包兼容基于 Scatter 接口开发的 DAPP，您只需要做一些移动端适配即可

Scatter接口的优点是通用性好，除了移动端在麦子钱包内直接使用，桌面端可以配合 [MathWallet Chrome浏览器](https://chrome.google.com/webstore/detail/math-wallet/afbcbjpbpfadlkmhmclhkeeodmamcflc) 使用，一套代码即可，另外开发时在桌面端比较容易调试。

#### API 文档

[https://github.com/mathwallet/math-eosjs](https://github.com/mathwallet/math-eosjs)

#### Scatter API 开发示例

MediShares 团队开发的 Scatter API 开发示例

[https://github.com/MediShares/scatter-eos-sample](https://github.com/MediShares/scatter-eos-sample)

如果您是 EOS 和 DAPP 新手，您可以通过这个代码仓库入门

[https://github.com/ericfish/EOS-Dev-Book](https://github.com/ericfish/EOS-Dev-Book)

#### 使用 Scatter 接口的应用

[DICE](https://betdice.one)

[Chintai](https://eos.chintai.io)

#### Scatter API 相关问题

Q: 钱包和PC端引入的 scatter.js 文件需要区分一下吗？

不需要，使用Scatter官方的 scatter.min.js 即可，PC端可以运行后，放到麦子钱包即可运行，做下移动端页面适配即可

Q: 如何在 DAPP 页面获取钱包信息、全屏、打开微信、横屏、当前语言等信息和操作？

可以通过 math-js-sdk: [https://github.com/mathwallet/math-js-sdk](https://github.com/mathwallet/math-js-sdk)

## Native DAPP 开发

### SimpleWallet 协议

您可以通过麦子钱包定制版 SimpleWallet 协议进行：

Native APP 跳转麦子钱包支付或合约签名。

目前 EOS骑士、鲸交所、Newdex、SpiderStore 等 Native APP 已经使用麦子所提供的 SimpleWallet 协议接口。

协议标准请查看：

[https://github.com/mathwallet/SimpleWallet](https://github.com/mathwallet/SimpleWallet)

注意：transferReq.blockchain 参数请传 eosio

#### SimpleWallet API 开发示例

麦子钱包团队开发了一套APP端调起麦子钱包进行支付的示例代码：

iOS – [https://github.com/mathwallet/MathWalletSDK-iOS](https://github.com/mathwallet/MathWalletSDK-iOS)

Android – [https://github.com/mathwallet/MathWalletSDK-Android](https://github.com/mathwallet/MathWalletSDK-Android)

#### 使用 SimpleWallet 接口的应用

[EOS骑士](http://eosknights.io)

[鲸交所](https://whaleex.com)

## 网页 DAPP 打开麦子钱包支付

支持手机浏览器网页通过链接的形式打开麦子钱包进行支付和合约签名。接口基于 SimpleWallet 协议麦子拓展版本：

[https://github.com/mathwallet/SimpleWallet](https://github.com/mathwallet/SimpleWallet)

示例DEMO和代码：

1 网页点击按钮，打开麦子钱包并支付

[http://developer.mathwallet.org/sample12/simple.html](http://developer.mathwallet.org/sample12/simple.html)

[https://github.com/mathwallet/math-eosjs/blob/master/eos/sample12/simple.html](https://github.com/mathwallet/math-eosjs/blob/master/eos/sample12/simple.html)

2 网页点击按钮，打开麦子钱包并跳转到 DAPP 页面

[http://developer.mathwallet.org/sample12/openurl.html](http://developer.mathwallet.org/sample12/openurl.html)

[https://github.com/mathwallet/math-eosjs/blob/master/eos/sample12/openurl.html](https://github.com/mathwallet/math-eosjs/blob/master/eos/sample12/openurl.html)

## 钱包扫码登录和支付

麦子钱包支持基于 SimpleWallet 的 EOS 钱包扫描登录和支付

协议标准请查看：

[https://github.com/mathwallet/SimpleWallet](https://github.com/mathwallet/SimpleWallet)

目前 Newdex 网页版已经使用该接口进行扫码登录。