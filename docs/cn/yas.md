# YAS DAPP 开发文档

## H5 DAPP 开发

### Scatter API（推荐）

麦子钱包兼容基于 Scatter 接口开发的 DAPP，您只需要做一些移动端适配即可

Scatter接口的优点是通用性好，除了移动端在麦子钱包内直接使用，桌面端可以配合 [MathWallet Chrome浏览器](https://chrome.google.com/webstore/detail/math-wallet/afbcbjpbpfadlkmhmclhkeeodmamcflc) 使用，一套代码即可，另外开发时在桌面端比较容易调试。

#### Scatter API 官方文档

[https://get-scatter.com/docs/setting-up-for-web-apps](https://get-scatter.com/docs/setting-up-for-web-apps)

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
