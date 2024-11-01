# Web3 Data and Login

### Web3 Data <a href="#web3-data" id="web3-data"></a>

The data stored on web3 is only transactional data, which means that every time a user sends or receives something, an entry is added to the global ledger of the blockchain.

However, it is also possible to add a link inside this transaction to a decentralized database like IPFS, Arweave, Ceramic, etc. These links are unique on the decentralized databases and can contain arbitrary extra information.

Until now, the most popular use case for storing extra data on decentralized databases is that of the assets of a Non-Fungible Token (NFT).

All data stored on the blockchain or on the decentralized databases is open and publicly visible by default, unless special mechanisms are employed to preserve the privacy.

To learn more about preserving privacy, read more information on [encrypted data streams.](https://docs.plurality.network/concepts/data-ownership#data-streams)

### Web3 Login <a href="#web3-login" id="web3-login"></a>

Web3 login refers to the process of creating and using a wallet on a blockchain. A wallet has a public key and private key which always needs to be stored in a secure offline space.

> One of the biggest challenges in web3 adoption is the average user’s lack of technical expertise in creating and managing wallets.

#### Easier Login Processes <a href="#easier-login-processes" id="easier-login-processes"></a>

It is now increasingly clear that the current wallet creation and login processes are too complicated for an average user, and therefore, techniques for easier login processes are now being developed. Two of these techniques are discussed here.

**Account Abstraction**

From a user perspective, account abstraction means that the technical details of blockchain wallets are concealed from the user, thus providing them with a better experience.

From a technical perspective, account abstraction has many different implementations based on different Ethereum Request for Comments (ERCs). These implementations allow for various features targeted to improve user experience including gas paymasters, multisig, social recovery, etc.

**Wallet Abstraction through OAuth**

Wallet abstraction through oAuth is a specific type of account abstraction where users can use their existing web2 logins to create a web3 wallet. Authentication is done via Oauth to ensure that the wallet user is indeed the owner of the web2 profile and then it is used for wallet creation.

This feature allows for a simple login workflow like on many web2 websites today where you can create a new profile using an existing profile.

Such a combination not only abstracts away the existence of a wallet for users but is also extremely familiar and easy for users to create a web3 account. Moreover, the recovery mechanism in this case is also straightforward. As long as the user has access to the web2 profile, they can also use their web3 wallet.

Plurality is focused on this kind of account abstraction to provide a good onboarding experience for users.
