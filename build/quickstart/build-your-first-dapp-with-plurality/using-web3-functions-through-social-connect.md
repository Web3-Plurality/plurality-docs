# Using web3 functions through Social Connect

Since the Metamask gets connected to the social connect, all web3 calls also need to be done through the social connect. To enable multi-page applications, we setup separate events to capture the responses.&#x20;

To call any blockchain function you need to do 3 steps:

1. Call the function
2. Setup the event that captures the response
3. Wire up that event in \<PluralitySocialConnect>&#x20;

{% hint style="info" %}
Want to jump directly to code? Checkout final code on [Git](https://github.com/Web3-Plurality/demo-application)
{% endhint %}

### Get all connected accounts

Returns all accounts that have been connected through the social connect

1. **Function Call**

```
PluralitySocialConnect.getAllAccounts() 

Returns: [0x123…, 0x456…]
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleGetAllAccounts = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Get all accounts:", receivedData);
    alert(JSON.stringify(data));
};
```

3. **Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onGetAllAccounts={handleGetAllAccounts}
    ...
/>
```

### Get Current Connected Account

Get current account connected to the social connect

1. **Function Call**

```
PluralitySocialConnect.getConnectedAccount() 

Returns: 0x123…
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleGetConnectedAccount = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Get connected account:", receivedData);
    alert(JSON.stringify(data));
};
```

3. **Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onGetConnectedAccount={handleGetConnectedAccount}
    ...
/>
```

### Get Signature

Gets the message signed using the connected account and returns the signature

1. **Function Call**

```
PluralitySocialConnect.getMessageSignature(message: string) 

Example:
PluralitySocialConnect.getMessageSignature("Example `personal_sign` message.")
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleMessageSignature = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Get message signature:", receivedData);
    alert(JSON.stringify(data));
};
```

**Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onGetMessageSignature={handleMessageSignature}
    ...
/>
```

### Verify Message Signature

Verify if the signature matches the message using the current connected account and returns boolean true or false

1. **Function Call**

```
PluralitySocialConnect.verifyMessageSignature(message: string, signature: string) 

Example: PluralitySocialConnect.verifyMessageSignature("Example `personal_sign` message.", "0xa1379711716d214c84c146bbaa9d03d77895526b8620bcae67a76f824be6fd3a43795645a31f758eaed39ee6aa5490a979233711d4e9d6a2e30fa09a5e9c808a1b")
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleVerifyMessageSignature = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Verify message signature:", receivedData);
    alert(JSON.stringify(data));
};
```

3. **Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onVerifyMessageSignature={handleVerifyMessageSignature}
    ...
/>
```

### Get Balance

Returns balance of the current account in wei. You need to convert it to required denomination yourself

1. **Function Call**

```
PluralitySocialConnect.getBalance()
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleGetBalance = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Get balance:", receivedData);
    alert(JSON.stringify(data));
};
```

3. **Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onGetBalance={handleGetBalance}
    ...
/>
```

### Send Transaction

Send a certain amount (in ethers) to a certain address. Returns the transaction object

1. **Function Call**

```
PluralitySocialConnect.sendTransaction(sendToAddress: string, value: string) 

Example:  PluralitySocialConnect.sendTransaction("0xe613B4cd69Fe20E8bd0F0D79a264210886bA1AA2","0.01")
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleSendTransaction = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Send transaction:", receivedData);
    alert(JSON.stringify(data));
};
```

3. **Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onSendTransaction={handleSendTransaction}
    ...
/>
```

### Get Block Number

Returns the latest block number

1. **Function Call**

```
PluralitySocialConnect.getBlockNumber()
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleGetBlockNumber = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Get block number:", receivedData);
    alert(JSON.stringify(data));
};
```

3. **Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onGetBlockNumber={handleGetBlockNumber}
    ...
/>
```

### Get Transaction Count

Returns the transaction count of the given address

1. **Function Call**

```
PluralitySocialConnect.getTransactionCount(address: string) 

Example: PluralitySocialConnect.getTransactionCount("0xe613B4cd69Fe20E8bd0F0D79a264210886bA1AA2")
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleGetTransactionCount = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Get transaction count:", receivedData);
    alert(JSON.stringify(data));
};
```

3. **Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onGetTransactionCount={handleGetTransactionCount}
    ...
/>
```

### Read From Contract

Returns the response of executing the given get method of the contract with the given parameters

1. **Function Call**

```
PluralitySocialConnect.readFromContract(contractAddress: string, abi: string, methodName: string, methodParams: string[]) 

Example:
   const abi = '[{"inputs":[],"name":"retrieve","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"num","type":"uint256"}],"name":"store","outputs":[],"stateMutability":"nonpayable","type":"function"}]';
PluralitySocialConnect.readFromContract("0x8E26aa0b6c7A396C92237C6a87cCD6271F67f937",abi,"retrieve", [])
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleReadFromContract = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Read from contract:", receivedData);
    alert(JSON.stringify(data));
};
```

3. **Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onReadFromContract={handleReadFromContract}
    ...
/>
```

### Write To Contract

Returns the transaction response of executing the given write method of the contract with the given parameters

1. **Function Call**

```
PluralitySocialConnect.writeToContract(contractAddress: string, abi: string, methodName: string, methodParam: string[]) 

Example:
   const abi = '[{"inputs":[],"name":"retrieve","outputs":[{"internalType":"uint256","name":"","type":"uint256"}],"stateMutability":"view","type":"function"},{"inputs":[{"internalType":"uint256","name":"num","type":"uint256"}],"name":"store","outputs":[],"stateMutability":"nonpayable","type":"function"}]';
PluralitySocialConnect.writeToContract("0x8E26aa0b6c7A396C92237C6a87cCD6271
```

2. **Response Capture Event**

The response will be received in the following event that needs to be registered in your application

```
const handleWriteToContract = (data) => {
    const receivedData = JSON.parse(JSON.stringify(data))
    console.log("Write to contract:", receivedData);
    alert(JSON.stringify(data));
};
```

3. **Wire Up The Event**

```
<PluralitySocialConnect
    ...
    onWriteToContract={handleWriteToContract}
    ...
/>
```
