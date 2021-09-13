# Solana

## Integrating

### Detecting the Provider

MathWallet will inject an object called`solana` on the [window](https://developer.mozilla.org/en-US/docs/Web/API/Window) object of any web application the user visits.

To detect if a browser extension using this API is installed, you can check for the existence of the `solana` object.

To make it easy to detect MathWallet specifically, the extension adds an additional `isMathWallet` flag.

![solana](http://qiniu.eth.fm/2021-07-28-solana.png)

```javascript
const isMathWalletInstalled = window.solana && window.solana.isMathWallet
```

If MathWallet is not installed, we recommend you redirect your users to [our website](https://mathwallet.org/). Altogether, this may look like the following.

```javascript
const getProvider = () => {
  if ("solana" in window) {
    const provider = window.solana;
    if (provider.isMathWallet) {
      return provider;
    }
  }
  window.open("https://mathwallet.org/", "_blank");
};
```

### Establishing a Connection

In order to start interacting with MathWallet you must first establish a connection. This connection request will prompt the user for permission to share their public key, and indicate that they are willing to interact further.

```javascript
window.solana.getAccount();
```

When the user has accepted the request to connect, the provider will emit a `connect` event.

```javascript
window.solana.getAccount()
      .then((account: any) => {
        this._publicKey = new PublicKey(account);
        this._connected = true;
        this.emit('connect', this._publicKey);
      })
      .catch(() => {
        this.disconnect();
      })
      .finally(() => {
        this._onProcess = false;
      });
```

Once the web application is connected, it will be able to read the connected account info

```javascript
window.solana.publicKey.toString()
// 2TE8zHirQSQ44ojJvnw9qBs5rjWFa5YJEF1EYyyutjbS 
window.solana.isConnected
// true
window.solana.autoApprove
// true or false
```

### Disconnecting

Disconnecting is similar to connecting, however, it is possible for the disconnection to originate from the wallet.

```javascript
window.solana.disconnect();
```

### Sending a Transaction

Once the web application is connected to MathWallet, it can send transactions on behalf of the user, with the user's permission.

In order to send a transaction, the web application must:

* Create an unsigned transaction or transactions.
* Have it be signed by the user's MathWallet.
* Send it to a Solana node for processing.

For more information about the nature of transactions on Solana, it is recommended to review the `solana-web3.js` [docs](https://solana-labs.github.io/solana-web3.js/class/src/transaction.js~Transaction.html) as well as the official [Solana docs](https://docs.solana.com/developing/programming-model/transactions).

```javascript
const network = "<NETWORK_URL>";
const connection = new Connection(network);
const transaction = new Transaction();
const signedTransaction = await window.solana.signTransaction(transaction);
const signature = await connection.sendRawTransaction(signedTransaction.serialize());
```

### Signing Multiple Transactions

It is also possible to sign and send multiple transactions at once. This is exposed through the `signAllTransactions` method on the provider.

```javascript
const signedTransactions = await window.solana.signAllTransactions(transactions);
```

### Signing a Message

When the web application is connected to MathWallet, it can also request that the user signs a given message. 

In order to send a message for the user to sign, the web application must: 

* Provide a hex or UTF-8 encoded string as a Uint8Array.
* Have it be signed by the user's MathWallet.

```javascript
const message = `Owner of punk #8888`;
const encodedMessage = new TextEncoder().encode(message);
const signedMessage = await window.solana.signMessage(encodedMessage, "utf8");
```


## SOL Wallet Adapter Samples (Multi-wallets Support)

You can reference serum dex or serum swap code which using the sol-wallet-adapter connects to multiple wallets

Such as: [https://dex.projectserum.com](https://dex.projectserum.com)

![](http://qiniu.eth.fm/2021-09-13-multiwallet.png)

SOL Wallet Adapter provided unified methods based on user's wallet selection

Front-end code can reference:

[https://github.com/project-serum/serum-dex-ui](https://github.com/project-serum/serum-dex-ui)

[https://github.com/project-serum/oyster-swap](https://github.com/project-serum/oyster-swap)

### Add MathWallet Related Config

If you are using the sol-wallet-adapter which allows your dapp connects to multiple wallets, here are the changes need for MathWallet:

Sample 1

[https://github.com/project-serum/oyster-swap/blob/master/src/wallet-adapters/math/index.tsx](https://github.com/project-serum/oyster-swap/blob/master/src/wallet-adapters/math/index.tsx)

[https://github.com/project-serum/oyster-swap/blob/master/src/context/wallet.tsx](https://github.com/project-serum/oyster-swap/blob/master/src/context/wallet.tsx)

Sample 2

[https://github.com/project-serum/serum-dex-ui/pull/63/files](https://github.com/project-serum/serum-dex-ui/pull/63/files)

Common errors in wallet.tsx config (which will cause the wallet cannot inject to the dapp site)

![mathso](http://qiniu.eth.fm/2021-09-01-mathsol2.jpg)

## More Resources

### solana-web3.js

[https://github.com/solana-labs/solana-web3.js](https://github.com/solana-labs/solana-web3.js)

### RPC document

[https://docs.solana.com/](https://docs.solana.com/)

[https://solanaproject.com/#/rpcserver](https://solanaproject.com/#/rpcserver)

### Fungible Tokens

SPL Token Registry

[https://github.com/solana-labs/token-list](https://github.com/solana-labs/token-list)

Submit to MathWallet

[https://m.maiziqianbao.net/submit/token?type=Solana](https://m.maiziqianbao.net/submit/token?type=Solana)


