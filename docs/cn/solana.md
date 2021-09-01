# Solana DAPP 开发文档

## H5 DAPP 开发

### RPC接口文档

[https://docs.solana.com/](https://docs.solana.com/)

### 钱包 Adapter API（用于与网页钱包或插件钱包通讯的模块）

[https://github.com/project-serum/sol-wallet-adapter](https://github.com/project-serum/sol-wallet-adapter)

### Web3 JS (前端组装交易的模块)

[https://github.com/solana-labs/solana-web3.js](https://github.com/solana-labs/solana-web3.js)

### 连接钱包 UI 的示例

[https://github.com/project-serum/serum-dex-ui](https://github.com/project-serum/serum-dex-ui)

[https://github.com/project-serum/oyster-swap](https://github.com/project-serum/oyster-swap)


### 添加 MathWallet 适配相关的代码修改

修改点 (如果你没有使用和参考最新版本的 sol-wallet-adapter 以及 ui 代码)

[https://github.com/project-serum/oyster-swap/blob/master/src/wallet-adapters/math/index.tsx](https://github.com/project-serum/oyster-swap/blob/master/src/wallet-adapters/math/index.tsx)

[https://github.com/project-serum/oyster-swap/blob/master/src/context/wallet.tsx](https://github.com/project-serum/oyster-swap/blob/master/src/context/wallet.tsx)

[https://github.com/project-serum/serum-dex-ui/pull/63/files](https://github.com/project-serum/serum-dex-ui/pull/63/files)

常见的 wallet.tsx 文件错误配置（会导致钱包无法完成注入操作）

![mathso](http://qiniu.eth.fm/2021-09-01-mathsol1.jpg)

![mathso](http://qiniu.eth.fm/2021-09-01-mathsol2.jpg)

