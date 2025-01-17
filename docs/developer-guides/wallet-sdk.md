# Wallet SDK

> This guide shows how to use standard web3 wallet functions&#x20;

Every wallet needs to interact with the blockchain for carrying out various functions. Once the widget is embedded and the user connects their profile through their preferred auth method, a session is created for this user after which the standard wallet functions can be utilized.

### AuthMethod

To create a wallet, user first needs to choose how do they want to create the wallet i.e. select their AuthMethod. Currently we support 3 auth methods (with support for more auth methods coming soon)   i.e. gmail, email and metamask.

Once the user selects a certain auth method, a wallet is created in the network that makes sure that this wallet is accessible only with a valid login jwt of the selected auth method.&#x20;

{% hint style="info" %}
If the user uses an email for creation of a wallet and then later on selects gmail for that same email address, we **do not** create two separate wallets rather tag both authmethods to the same user. Currently no other embedded wallet products offer this feature, resulting in users regularly forgetting what they used to sign up to an application. We reduce this cognitive load for end users.
{% endhint %}

### ProfileSession

After successful login of profile, a session is created that allows user to access the SDK functions. The session expires after a certain time or when the user logs out. Without valid session signatures, the MPC network will not allow for signature signing.&#x20;

## Wallet SDK

To access the wallet functions, the following import should be done on the page/component where the functions need to be called.

```
import { PluralitySocialConnect } from '@plurality-network/smart-profile-wallet';
```

Once the application has access to a valid session i.e. the user has successfully logged in, the following wallet functions become accessible. \


### Get All Connected Accounts

Returns all connected accounts/addresses e.g. \[0x123…, 0x456…].&#x20;

```typescript
const response = (await PluralitySocialConnect.getAllAccounts()) as AllAccountsDataType;

if (response) {
    const allAccounts = response.data;
    return allAccounts[0]?.address;
}
```

### Get Current Connected Account

Get current account connected

```typescript
const response = (await PluralitySocialConnect.getConnectedAccount()) as ConnectedAccountDataType;

if (response) {
    const connectedAccount = response.data;
    return connectedAccount?.address;
}
```

### Get Signature

Gets the message signed using the connected account and returns the signature.

```typescript
const response = (await PluralitySocialConnect.getMessageSignature(message)) as SignMessageDataType;
if (response) {
    const signMessage = response.data;
    return signMessage;
}
```

### Verify Message Signature

Verify if the signature matches the message using the current connected account and returns boolean true or false.

```typescript
const response = (await PluralitySocialConnect.verifyMessageSignature(message, key)) as VerifySignedMessageDataType;
if (response) {
    const verifyMessage = response.data;
    return verifyMessage;
}
```

### Get Balance

Returns balance of the current account in wei. You need to convert it to the required denomination yourself.&#x20;

{% hint style="info" %}
Please note that since Plurality profiles are chain agnostic, you need to provide the RPC and the chainId to ensure that balance is being read from the current read. You can find the RPC and the chainId of your preferred chain through this [link](https://chainlist.org/). We currently support only EVM-compatible chains.&#x20;
{% endhint %}

```typescript
const response = (await PluralitySocialConnect.getBalance(rpc, chainId)) as GetBalanceDataType;
if (response) {
    const getBalance = response.data;
    return getBalance;
}
```

### Send Transaction

Send a certain amount (in ethers) to a certain address. Returns the transaction object.

{% hint style="info" %}
Please note that since Plurality profiles are chain agnostic, you need to provide the RPC and the chainId to ensure that balance is being read from the current read. You can find the RPC and the chainId of your preferred chain through this [link](https://chainlist.org/). We currently only support EVM-compatible chains.
{% endhint %}

```typescript
const response = (await PluralitySocialConnect.sendTransaction(rawTx, rpc, chainId)) as SendTransactionDataType;
if (response) {
    const sendTransactionData = response.data;
    return sendTransactionData;
}
```

### Get Block Number

Returns the latest block number.

```typescript
const response = (await PluralitySocialConnect.getBlockNumber(rpc, chainId)) as GetBlockNumberDataType;
if (response) {
    const blockNumber = response.data;
    return blockNumber;
}
```

### Get Transaction Count

Returns the transaction count of the given address

```typescript
const response = (await PluralitySocialConnect.getTransactionCount(address, rpc, chainId)) as GetTransactionCountDataType;
if (response) {
    const transactionCount = response.data;
    return transactionCount;
}
```

### Read from contract

Returns the response of executing the given get method of the contract with the given parameters

```typescript
const response = (await PluralitySocialConnect.readFromContract(address, abiVal, action, params, rpc, chainId)) as ReadFromContractDataType;
if (response) {
    const readContract = response.data;
    return readContract;
}
```

### Write to contract

Returns the transaction response of executing the given write method of the contract with the given parameters

```typescript
const response = (await PluralitySocialConnect.writeToContract(address, abiVal, action, params, rpc, chainId, options)) as WriteToContractDataType;
if (response) {
    const writeContract = response.data;
    return writeContract;
}
```

{% hint style="info" %}
Didn't find what you were looking for? Contact us on discord [here](https://discord.com/invite/Mb6ZDgGjcP).
{% endhint %}
