# Substrate

This applies to all Substrate based blockchains, including Polkadot, Kusama, Acala, Statemine, MathChain L1, etc

The only differences for these chains are the ChainID and Node Endpoint which can be found here:

[https://polkadot.js.org/apps/](https://polkadot.js.org/apps/)

## Integrating (Web)

### Detecting the Provider

MathWallet will inject an object called `injectedWeb3` on the [window](https://developer.mozilla.org/en-US/docs/Web/API/Window) object of any web application the user visits.

To detect if a browser extension using this API is installed, you can check for the existence of the `injectedWeb3` object.

To make it easy to detect MathWallet specifically, the extension adds an additional `mathWallet` flag.

![math](http://qiniu.eth.fm/2021-07-28-dot.png)

```javascript
const isMathWalletInstalled = window.injectedWeb3 && window.injectedWeb3.mathWallet
```

If MathWallet is not installed, we recommend you redirect your users to [our website](https://mathwallet.org/).

### Establishing a Connection

First import polkadotjs and extension related packages

```javascript
import {
	isWeb3Injected,
	web3Accounts,
	web3Enable,
	web3FromAddress
} from "@polkadot/extension-dapp";
web3Enable('polkadot-js/apps');
```

In order to start interacting with MathWallet you must first establish a connection. "Connecting" to MathWallet on substrate chains effectively means "to access the user's substrate account(s)".

```javascript
/***
 * login
 * @return accounts [{"address":"5D2JMakX2CgtPPkiqUzdsK3Y41vD6HyNy8ZETUjhjRrZFTfG","meta":{"name":"cc1","source":"polkadot-js"}}]
 */
async login() {
	if (!isWeb3Injected) {
		throw new Error("Please install/unlock the MathWallet first");
	}
	// meta.source contains the name of the extension that provides this account
	const allAccounts = await web3Accounts();
	return allAccounts;
}
```

For mobile it will only return one account, but for extension it may return multiple accounts as array.

### Sending a Transaction

Once the web application is connected to MathWallet, it can send transactions on behalf of the user, with the user's permission.

In order to send a transaction, the web application must:

* Connect to WsProvider
* Create an unsigned transaction or transactions.
* Have it be signed by the user's MathWallet.

For more information about the nature of transactions on Substrate, it is recommended to review the `polkadotjs` [docs](https://polkadot.js.org/docs/).

```javascript
const { ApiPromise, WsProvider } = require('@polkadot/api');

/***
 * Transfer
 * @param from from
 * @param to to
 * @param amount amount
 * @return hash
 */
async transfer(from, to, amount) {
	// Initialise the provider to connect to the local node
	const provider = new WsProvider('wss://rpc.polkadot.io');
	
	// Create the API and wait until ready
	const api = await ApiPromise.create({ provider });

	// finds an injector for an address
	const injector = await web3FromAddress(from);

	// sets the signer for the address on the @polkadot/api
	api.setSigner(injector.signer);

	// sign and send out transaction - notice here that the address of the account (as retrieved injected)
	// is passed through as the param to the `signAndSend`, the API then calls the extension to present
	// to the user and get it signed. Once completex, the api sends the tx + signature via the normal process
	const h = api.tx.balances
		.transfer(to, amount)
		.signAndSend(from);

	return h;
}
```

## More Resources

### Sample by MathWallet (Login & Sign Transactions)

[https://github.com/mathwallet/math-substratejs](https://github.com/mathwallet/math-substratejs)

### Polkadot Wiki

[https://wiki.polkadot.network/docs/getting-started](https://wiki.polkadot.network/docs/getting-started)

### Developer Resources

[https://www.polkaproject.com/#/projects?cateID=6](https://www.polkaproject.com/#/projects?cateID=6)

