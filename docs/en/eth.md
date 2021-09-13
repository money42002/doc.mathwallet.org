# EVM

This applies to all EVM based blockchains, including Ethereum, BSC, Arbitrum, Polygon, Fantom, Moonbeam, MathChain L2, etc

The only difference for these chains is the ChainID & RPC which can be query here:

[https://chainlist.org/](https://chainlist.org/)

[https://chainid.network/chains.json](https://chainid.network/chains.json)

## Integrating (Web)

### Detecting the Provider

MathWallet will inject an object called `ethereum` on the [window](https://developer.mozilla.org/en-US/docs/Web/API/Window) object of any web application the user visits.

To detect if a browser extension using this API is installed, you can check for the existence of the `ethereum` object.

To make it easy to detect MathWallet specifically, the extension adds an additional `isMathWallet` flag.

![eth](http://qiniu.eth.fm/2021-07-28-eth.png)

```javascript
const isMathWalletInstalled = window.ethereum && window.ethereum.isMathWallet
```

If MathWallet is not installed, we recommend you redirect your users to [our website](https://mathwallet.org/). Altogether, this may look like the following.

```javascript
const getProvider = () => {
  if ("ethereum" in window) {
    const provider = window.ethereum;
    if (provider.isMathWallet) {
      return provider;
    }
  }
  window.open("https://mathwallet.org/", "_blank");
};
```

### Establishing a Connection

In order to start interacting with MathWallet you must first establish a connection. "Connecting" to MathWallet on EVM chains effectively means "to access the user's EVM account(s)".

```javascript
const accounts = await ethereum.request({ method: 'eth_requestAccounts' });
const account = accounts[0];
```

### Sending a Transaction

Once the web application is connected to MathWallet, it can send transactions on behalf of the user, with the user's permission.

In order to send a transaction, the web application must:

* Create an unsigned transaction or transactions.
* Have it be signed by the user's MathWallet.
* Send it to a RPC node for processing.

For more information about the nature of transactions on Ethereum, it is recommended to review the `web3js` [docs](https://web3js.readthedocs.io/) as well as the [Metamask docs](https://docs.metamask.io/guide/sending-transactions.html#example).

```javascript
const transactionParameters = {
  nonce: '0x00', // ignored by MathWallet
  gasPrice: '0x09184e72a000', // customizable by user during MathWallet confirmation.
  gas: '0x2710', // customizable by user during MathWallet confirmation.
  to: '0x0000000000000000000000000000000000000000', // Required except during contract publications.
  from: ethereum.selectedAddress, // must match user's active address.
  value: '0x00', // Only required to send ether to the recipient from the initiating external account.
  data:
    '0x7f7465737432000000000000000000000000000000000000000000000000000000600057', // Optional, but used for defining smart contract creation and interaction.
  chainId: '0x3', // Used to prevent transaction reuse across blockchains. Auto-filled by MathWallet.
};

// txHash is a hex string
// As with any RPC call, it may throw an error
const txHash = await ethereum.request({
  method: 'eth_sendTransaction',
  params: [transactionParameters],
});
```

### Signing a Message

When the web application is connected to MathWallet, it can also request that the user signs a given message. 

```javascript
// Create a SHA3 hash of the message 'Apples'
const messageHash = web3.sha3('Owner of punk #8888');

// Signs the messageHash with a given account
const signature = await web3.eth.personal.sign(messageHash, web3.eth.defaultAccount);
```

## Integrating (Native dApp)

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


## More Resources

### Ethereum Developer Docs

[https://ethereum.org/en/developers/docs/](https://ethereum.org/en/developers/docs/)

### Fungible Tokens

ERC20 Token Registry

[https://tokenlists.org/](https://tokenlists.org/)

Submit to MathWallet

[https://m.maiziqianbao.net/submit/token?type=](https://m.maiziqianbao.net/submit/token?type=)


