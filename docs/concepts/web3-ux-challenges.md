# Web3 UX Challenges

## Web3 <a href="#web3" id="web3"></a>

We discussed previously about how Web1 was the static, read-only internet and Web2 is the dynamic, read-and-write internet.

Web3 is a technological successor to Web2, where not only is it possible to read and write data, but also to _own_ data.

> Web3 allows users to own a piece of the web

On web3, every action-doer is a wallet address, which is nothing more than a hexadecimal string of characters, controlled by a set of public and private key pairs.

Using a wallet, whatever state update is made is added to a global ledger which is transparent, open, decentralized, and immutable. Similarly, when content is created by a wallet, the origin of where and how the content was produced it is publicly verifiable.

This opens the doors for a new age of internet.

### Challenges of Web3 <a href="#challenges-of-web3" id="challenges-of-web3"></a>

Web3 has started a global revolution, but since the technology is still in its nascent stages, there are currently many challenges facing Web3, especially in the area of user experience. We will discuss a few of those here.

> User experience is the overall experience of a person using a product such as a website or computer application, especially in terms of how easy or pleasing it is to use.

#### Wallet Creation <a href="#wallet-creation" id="wallet-creation"></a>

Wallet creation in web3 is very different as compared to creating a profile on web2. The user needs to install new wallets, face clunky UIs, and then be asked to store seed phrases securely otherwise they will lose access to not only their wallet but also any funds (cryptocurrency) that they hold in that wallet.

> Complicated onboarding process is the leading cause of churning users on web3

More often than not, this scares away the users, especially those from non-tech backgrounds. An alternative way to create wallets is on an exchange, but that opposes the ethos of web3 where users are in full control and gives exchanges the access to meddle with user funds.

> Not your keys, not your crypto

A balance between easy onboarding and true ownership of users is the key to creating a better user experience.

#### Wallet Recovery <a href="#wallet-recovery" id="wallet-recovery"></a>

If the user loses the seed phrase, it is impossible to recover the wallet unless the user sets up some form of wallet recovery mechanism. Setting up a recovery mechanism also involves complicated setups like multi-sig, storing in software like KeePass, or getting a hardware wallet and setting up with a pin. Again, an easier wallet recovery option (that does not delegate the ownership of the wallet to someone else) is required for a balance between user experience and true wallet ownership.

{% hint style="warning" %}
Lost seed phrases have resulted in the loss of 20% of bitcoin in circulation – [a percentage some analysts value at roughly $140 billion](https://www.nytimes.com/2021/01/13/business/tens-of-billions-worth-of-bitcoin-have-been-locked-by-people-who-forgot-their-key.html).
{% endhint %}

Creating wallets through Multi-Party Compute is one way of creating self-custodial wallets with easy login workflows.&#x20;

#### Gas <a href="#lack-of-context" id="lack-of-context"></a>

Gas is a concept unique to web3 introduced by Ethereum and now is a norm in web3 space. In order to maintain a decentralized verifiable ledger for the world, there needs to be enough incentive for the nodes to do that effort. That incentive comes in the form of gas.&#x20;

Every time there needs to be a transaction in web3, gas needs to be paid.&#x20;

The problem? Every blockchain's gas is in its native token. For example, to do actions on Ethereum's platform, the gas needs to be paid in ETH, to do some actions on Solana, the gas needs to be paid in SOL and so on.

This means that users need to maintain balances of different tokens in their different wallets if they want to use platforms on that particular chain.&#x20;

> How the gas experience would feel like in the real world:\
> You need to have 5 different purses when you go out, each of these purses needs to have a different currency. When you go to shop A, you open your purse A and use the currency A to pay there. When you go to shop B, you would open your purse B to pay with currency B.&#x20;

This is how clunky the gas experience is right now. Initiatives like Gas abstraction and payment through Stablecoins is one step in the right direction. But overall, the gas should be completely abstracted away from the end user.

#### Data Poverty <a href="#lack-of-context" id="lack-of-context"></a>

Until now, the data being stored against a wallet is mostly financial like buying/selling tokens & NFTs.

> Web3 wallets are nothing more than a bank account for now

However, if we compare this behavior with web2 platforms, we can see that there is a lot more context about the user stored against the user profiles. Using this context, the platforms provide a personalized experience to the user. For example:

1. If a user regularly listens to songs from a certain artist, they will see suggestions of more songs from that same artist
2. If a user has done projects in Typescript, they will see more gigs related to Typescript
3. If a user has joined a certain kind of community, they will get recommendations to join other similar communities

etc.

These interactions with a platform increase user engagement and enable them to have a meaningful experience on a platform. But, this is only possible if the platform has this information that it can use to tweak the experience for a certain user.

Web3 currently does not store any such data and due to this, it does not have the means to provide for such a personalized experience.

> The current yearly user retention rate on web3 dApps is merely 7%

One way could be to create web3 platforms that store such data and then wait for people to come and interact with the platform and then after that will it be able to provide a good experience.

But this is a cyclical problem, also known as the _Cold Start Problem._

Platforms cannot provide a good experience without users using the platform. And users would not use the platform unless there is a good experience. And this is one of the biggest challenges of web3 dApps right now.

One approach to handle this would be to create reusable and portable contexts that could be taken to any dApp on any blockchain, which is what Plurality aims to do.

#### Lack of Network Effects <a href="#lack-of-network-effects" id="lack-of-network-effects"></a>

Platforms grow with communities and network effects. However, communities cannot be formed unless it is known what a certain user is interested in and what their social graph is.

One of the biggest growth reasons for web2 was the use of network effects. However, network effects are not yet possible to be created in web3 because only the data of financial transactions does not tell much about the user.

Once we link the interests and social graph of a user to their wallet, the creation of communities and consequently network effects will be easier to achieve.

While linking user information to their wallet, it is important to preserve the user's privacy, since data by default is transparent on the blockchain.
