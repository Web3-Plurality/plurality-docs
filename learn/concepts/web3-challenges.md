# 🌍 Web3 Challenges

## Web3

We already [discussed ](web2-data-and-login/#web1-and-web2)about how Web1 was the static, read-only internet and Web2 is the dynamic, read-and-write internet.

Web3 is a technological successor to Web2, where not only is it possible to read and write data, but also to _own_ data.&#x20;

> Web3 allows users to own a piece of the internet

On web3, every action-doer is a wallet address, which is nothing more than a hexadecimal string of characters, controlled by a set of public and private key pairs.&#x20;

Using a wallet, whatever state update is made is added to a global ledger which is transparent, open, decentralized, and immutable. Similarly, when content is created by a wallet, the origin of where and how the content was produced it is publicly verifiable.&#x20;

This opens the doors for a new age of internet.&#x20;

## Challenges of Web3

Web3 has started a global revolution, but since the technology is still in its nascent stages, there are currently many challenges facing Web3, especially in the area of user experience. We will discuss a few of those here.&#x20;

> User experience is the overall experience of a person using a product such as a website or computer application, especially in terms of how easy or pleasing it is to use.

### Wallet Creation

Wallet creation in web3 is very different as compared to creating a profile on web2. The user needs to install new wallets, face clunky UIs, and then be asked to store seed phrases securely otherwise they will lose access to not only their wallet but also any funds (cryptocurrency) that they hold in that wallet.&#x20;

> Complicated onboarding process is the leading cause of churning users on web3

More often than not, this scares away the users, especially those from non-tech backgrounds. An alternative way to create wallets is on an exchange, but that opposes the ethos of web3 where users are in full control and gives exchanges the access to meddle with user funds.

> Not your keys, not your crypto

A balance between easy onboarding and true ownership of users is the key to creating a better user experience.

### Wallet Recovery

If the user loses the seed phrase, it is impossible to recover the wallet unless the user sets up some form of wallet recovery mechanism. Setting up a recovery mechanism also involves complicated setups like multi-sig, storing in software like KeePass, or getting a hardware wallet and setting up with a pin. Again, an easier wallet recovery option (that does not delegate the ownership of the wallet to someone else) is required for a balance between user experience and true wallet ownership.&#x20;

### Lack of Context

Until now, the data being stored against a wallet is mostly financial like buying/selling tokens & NFTs.&#x20;

> Web3 wallets are nothing more than a bank account for now

However, if we compare this behavior with web2 platforms, we can see that there is a lot more context about the user stored against the user profiles. Using this context, the platforms provide a personalized experience to the user. For example:

1. If a user regularly listens to songs from a certain artist, they will see suggestions of more songs from that same artist
2. If a user has done projects in Typescript, they will see more gigs related to Typescript
3. If a user has joined a certain kind of community, they will get recommendations to join other similar communities

etc.

These interactions with a platform increase user engagement and enable them to have a meaningful experience on a platform. But, this is only possible if the platform has this information that it can use to tweak the experience for a certain user.

Web3 currently does not store any such data and due to this, it does not have the means to provide for such a personalized experience.&#x20;

> The current yearly user retention rate on web3 dApps is merely 7%

One way could be to create web3 platforms that store such data and then wait for people to come and interact with the platform and then after that will it be able to provide a good experience.

But this is a cyclical problem, also known as the _Cold Start Problem._&#x20;

Platforms cannot provide a good experience without users using the platform. And users would not use the platform unless there is a good experience.  And this is one of the biggest challenges of web3 dApps right now.&#x20;

One approach to handle this would be to create reusable and portable contexts that could be taken to any dApp on any blockchain, which is what Plurality aims to do.&#x20;

### Lack of Network Effects

Platforms grow with communities and network effects. However, communities cannot be formed unless it is known what a certain user is interested in.&#x20;

One of the biggest growth reasons for web2 was the use of network effects. However, network effects are not yet possible to be created in web3 because only the data of financial transactions does not tell much about the user.

Once we link the interests of a user to their wallet, the creation of interest-based communities and consequently network effects will be easier to achieve.&#x20;

{% hint style="info" %}
While linking user information to their wallet, it is important to preserve the user's privacy, since data by default is transparent on the blockchain.  To learn more about how this can be possible, see concepts of [zero-knowledge proofs](data-ownership.md#zero-knowledge-proofs) and [data streams](data-ownership.md#data-streams).
{% endhint %}
