# Using web3 functions through Social Connect

Since the Metamask gets connected to the social connect, all web3 calls also need to be done through the social connect. You can use the following functions to call the blockchain layer:

{% hint style="info" %}
Want to jump directly to code? Checkout final code on [Git](https://github.com/Web3-Plurality/demo-application)
{% endhint %}

#### Get All Connected Accounts

Returns all accounts that have been connected through the social connect

```
PluralitySocialConnect.getAllAccounts() 

Returns: [0x123…, 0x456…]
```

#### Get Current Connected Account

Get current account connected to the social connect

```
PluralitySocialConnect.getConnectedAccount() 

Returns: 0x123…
```

#### Get Signature

Gets the message signed using the connected account and returns the signature

```
PluralitySocialConnect.getMessageSignature(message: string) 

Example:
PluralitySocialConnect.getMessageSignature("Example `personal_sign` message.")
```

#### Verify Message Signature

Verify if the signature matches the message using the current connected account and returns boolean true or false

```
PluralitySocialConnect.verifyMessageSignature(message: string, signature: string) 

Example: PluralitySocialConnect.verifyMessageSignature("Example `personal_sign` message.", "0xa1379711716d214c84c146bbaa9d03d77895526b8620bcae67a76f824be6fd3a43795645a31f758eaed39ee6aa5490a979233711d4e9d6a2e30fa09a5e9c808a1b")
```

#### Get Balance

Returns balance of the current account in wei. You need to convert it to required denomination yourself

```
PluralitySocialConnect.getBalance()
```

#### Send Transaction

Send a certain amount (in ethers) to a certain address. Returns the transaction object

```
PluralitySocialConnect.sendTransaction(sendToAddress: string, value: string) 

Example:  PluralitySocialConnect.sendTransaction("0xe613B4cd69Fe20E8bd0F0D79a264210886bA1AA2","0.01")
```

#### Get Block Number

Returns the latest block number

```
PluralitySocialConnect.getBlockNumber()
```

#### Get Transaction Count

Returns the transaction count of the given address

```
PluralitySocialConnect.getTransactionCount(address: string) 

Example: PluralitySocialConnect.getTransactionCount("0xe613B4cd69Fe20E8bd0F0D79a264210886bA1AA2")
```

#### Read from contract

Returns the response of executing the given get method of the contract with the given parameters

```
PluralitySocialConnect.readFromContract(contractAddress: string, abi: string, methodName: string, methodParams: string[]) 

Example:
   const abi = '[{"inputs":[],"name":"retrieve","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"num","type":"uint256"}],"name":"store","outputs":[],"stateMutability":"nonpayable","type":"function"}]';
PluralitySocialConnect.readFromContract("0x8E26aa0b6c7A396C92237C6a87cCD6271F67f937",abi,"retrieve", [])
```

#### Write to contract

Returns the transaction response of executing the given write method of the contract with the given parameters

```
PluralitySocialConnect.writeToContract(contractAddress: string, abi: string, methodName: string, methodParam: string[]) 

Example:
   const abi = '[{"inputs":[],"name":"retrieve","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"num","type":"uint256"}],"name":"store","outputs":[],"stateMutability":"nonpayable","type":"function"}]';
PluralitySocialConnect.writeToContract("0x8E26aa0b6c7A396C92237C6a87cCD6271
```
