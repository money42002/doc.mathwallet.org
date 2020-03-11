# YAS DAPP Development Document

## Web dApp Development

### Scatter API

Math Wallet is compatiable with Scatter API.

ScatterJS is really universal that could not only be used with [MathWallet Chrome Extension](https://chrome.google.com/webstore/detail/math-wallet/afbcbjpbpfadlkmhmclhkeeodmamcflc) on desktop but also could be used directly inside mobile terminal such as Math Wallet with just one set of code. By the way, it would be much easier to debug on desktop during development.

#### Scatter API Official Doc

[https://get-scatter.com/docs/setting-up-for-web-apps](https://get-scatter.com/docs/setting-up-for-web-apps)

#### Scatter API Demo Projects

Scatter API Sample developed by MediShares Team

[https://github.com/MediShares/scatter-eos-sample](https://github.com/MediShares/scatter-eos-sample)

Sample project for EOS newbie

[https://github.com/ericfish/EOS-Dev-Book](https://github.com/ericfish/EOS-Dev-Book)

#### dApps using Scatter API

[DICE](https://betdice.one)

[Chintai](https://eos.chintai.io)

#### Scatter API QA

Q. Is it neccessary to distinguish the sactter.js file from wallet or PC side?

A. No, just use 'scatter.min.js'. PC side could run first and then put into Math Wallet and make some mobile adaptation.

Q. How to get more current wallet information, such as orientation / language / fullscreen, etc?

A. We will need math-js-sdk: [https://github.com/mathwallet/math-js-sdk](https://github.com/mathwallet/math-js-sdk)
