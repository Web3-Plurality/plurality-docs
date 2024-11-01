# Login

## Web3 Login <a href="#web3-login" id="web3-login"></a>

Web3 login refers to the process of creating and using a wallet on a blockchain. A wallet has a public key and private key which always needs to be stored in a secure offline space.

For doing any transaction, the private key is required to sign the data of the transaction. The trust assumption is that this private key is only known to the user and no one else, and if it is cryptographically proved that the transaction is signed by the user's private key, then we can be sure that the user intended this transaction to happen.

However, in order to fulfill this trust assumption, user must always keep this private key or the seed-phrase in a secure place. A place that is ideally airgapped and cannot be stolen by anyone. This, however, creates friction.

> One of the biggest challenges in web3 adoption is the average user’s lack of technical expertise in creating and managing wallets.

### **The Concept of Custody** <a href="#easier-login-processes" id="easier-login-processes"></a>

Before we understand different kinds of ways that a wallet can be created and logged into, we need to understand the concept of custody.

Custody essentially means who has access to the private key. Initially, when blockchains started, there was only one possible way: self-custody.&#x20;

#### **Self-Custodial Wallets** <a href="#easier-login-processes" id="easier-login-processes"></a>

Users could create wallets and store seed-phrases somewhere safe. Since no intermediary had access to this seed-phrase and it was never stored on any centralized servers, therefore, it was cryptographically impossible for any malicious entity to sign any transaction or move any assets on user's behalf. This was difficult for non-technical users and loss of seed-phrases have to-date resulted in loss of billions of dollars. However, self-custody is freedom from all intermediaries and aligns with the core ethos of web3.

**Custodial Wallets**

As crypto started becoming mainstream, more and more non-technical users started buying it as an investment asset. However, seed-phrases were consistently proving to be a friction point for users. To solve this, companies e.g. exchanges started providing custodial wallet services where they hold the keys for you, but promised to never misuse your funds - similar to the promise that the banks do with people. To further strengthen the promise and to protect the regular people, several regulations came out as well and every company that wanted to provide these services had to get licenses before operating in the open market.&#x20;

It worked out fine for a few users until major scandals of consumer's crypto being misused came out, proving the old adage once again that `not your keys, not your crypto`.

The big question is, can there ever be a balance between self-custody and easier login processes? Let's find out.

### Easier Login Processes <a href="#easier-login-processes" id="easier-login-processes"></a>

It is now increasingly clear that the current wallet creation and login processes are too complicated for an average user, and therefore, techniques for easier login processes are now being developed. Two of these techniques are discussed here.

**Account Abstraction**

From a user perspective, account abstraction means that the technical details of blockchain wallets are concealed from the user, thus providing them with a better experience.

From a technical perspective, account abstraction has many different implementations based on different Ethereum Request for Comments (ERCs). These implementations allow for various features targeted to improve user experience including gas paymasters, multisig, social recovery, etc.&#x20;

The most prevalent implementation of Account Abstraction is Smart Accounts, which creates a smart contract for each wallet that has extra features targeted to improve user experience.

However, it depends who is the controller of this Smart Account - it could be a wallet, a web2 profile, a ledger, or any combination of the above.

**Social Logins**

Social logins is a specific type of wallet abstraction where users can use their existing web2 logins to create a web3 wallet. Authentication is done via Oauth to ensure that the wallet user is indeed the owner of the web2 profile and then it is used for wallet creation.

This feature allows for a simple login workflow like on many web2 websites today where you can create a new profile using an existing profile.

Such a combination not only abstracts away the existence of a wallet for users but is also extremely familiar and easy for users to create a web3 account. Moreover, the recovery mechanism in this case is also straightforward. As long as the user has access to the web2 profile, they can also use their web3 wallet.

However, the devil is in the details. Even within social logins, there are multiple ways to achieve this. Smart Accounts are one way but come with multiple technical challenges of their own, not to mention the gas cost that comes with deploying a new smart contract for each new account.

There is, however, another way, to achieve the same results.

**Multi-Party Compute**

> Multi-party computation (MPC) is a cryptographic technique that allows multiple parties to jointly compute a function over their inputs while keeping those inputs private. MPC ensures that no single party learns anything about the other parties' inputs beyond what can be inferred from the final output of the computation.

In simple terms, MPC creates private key in a way that it is split across multiple entities and no entity ever learns anything about the entire private key.&#x20;

There is a specific condition that needs to be satisfied in order for the network to be able to sign a transaction. If this condition is that the user must login to their web2 profile and provide a correct jwt, then this essentially could be used for creating wallets through social login. The underlying technique used to do it in a secure way is called [Threshold Cryptography](https://blog.pantherprotocol.io/threshold-cryptography-an-overview/)

{% hint style="info" %}
MPC wallets created through Social Login are **Self-Custodial Wallets**
{% endhint %}

Plurality's smart profiles are built on an MPC network tied to user's profiles or wallet - depending on their choice of controller.
