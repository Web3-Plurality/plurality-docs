# Data Ownership

When a person goes online and produces a digital footprint, who owns this data? The platform where this data is generated or the user? This is a decades-long question that has been discussed on various forums over the years and in this section, we will discuss it some more.

### Ownership: The difference between web2 and web3 <a href="#ownership-the-difference-between-web2-and-web3" id="ownership-the-difference-between-web2-and-web3"></a>

The biggest differentiator between web2 (traditional internet) and web3 (blockchain networks) was the user’s ability to truly own something on the web. This is why Non-Fungible Tokens (NFTs) caught so much hype over the last years because never in the history of the web were users ever truly able to own their data.

The data you produce on the web2 can be edited or removed without your consent if the platform you produced it on deems it so. With the new revolution of the web, we need better models for data ownership for users as well. Plurality’s mission is to make users truly own their data.

### User context in web2 <a href="#user-context-in-web2" id="user-context-in-web2"></a>

Every user that interacts on web2 platforms creates a context specific to that platform. For example, on social media platforms, you are constantly updating your interests and profile by viewing, sharing, or posting content. This context is specific to this platform and is stored on the platform’s server side. It is used to provide users with a personalized experience relevant to their personality or tastes.

### Server side state v/s client side state <a href="#server-side-state-v-s-client-side-state" id="server-side-state-v-s-client-side-state"></a>

A traditional web2 platform has three layers: frontend, backend, and storage. The frontend is also called the client side whereas the backend is also called as server side and holds all the business logic.

All the interactions that you make on a web2 platform create the user context and it is sent to the backend where it gets processed and ultimately stored in a centralized storage.

A traditional web3 platform has different layers: a frontend, a wallet, a smart contract, and decentralized storage.

The wallet is on the user’s end-device which interacts with the smart contracts via the frontend. The interaction with smart contracts creates blockchain transactions and sometimes extra data gets stored on decentralized storage like IPFS linked to this transaction.

Since plurality wants to bring the user’s data from web2 and link it to the web3 account, it intends to do so keeping the ethos of web3 intact and keeping the state client-side.

<figure><img src="https://docs.plurality.network/~gitbook/image?url=https%3A%2F%2F351514635-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FBMDJ9SC06J7dWtuKBrmK%252Fuploads%252FkNanCCL6Jge5KwtXxC9k%252FPicture1.png%3Falt%3Dmedia%26token%3De213fefb-757a-4a71-91d0-4b3cf306d3e1&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=9374de34&#x26;sv=1" alt=""><figcaption><p>Plurality moves the user state from server-side to client-side</p></figcaption></figure>

Plurality wants to store the user’s data in a way that it is controllable from the user’s wallet and shared with dApps on the end user device e.g., a browser.

### Data Sovereignty & Decentralized Identifier (DID) <a href="#data-sovereignty-and-decentralized-identifier-did" id="data-sovereignty-and-decentralized-identifier-did"></a>

Data sovereignty is a concept that goes beyond simply ownership of data. Data sovereignty means the ability to choose when, to whom, and how much data is being shared.

A decentralized Identifier (DID) is an identifier that helps establish data sovereignty by linking data pieces to DIDs and revealing the data only when the user wants. There are several different DID methods but the one that is used by Plurality is the did:key method which allows users to create several distinct DIDs against a single wallet address.

Creating several DIDs against one address provides correlation resistance. Correlation resistance is important so that the distinct pieces of data are linked to different DIDs which are then linked to the wallet. If a malicious entity somehow figures out content against one DID, they would not be able to figure out the other DIDs associated with this account. The correlation resistance is an essential feature in preserving user’s privacy.

### Data Streams <a href="#data-streams" id="data-streams"></a>

The data stored against DIDs are stored in data streams that are under the user’s control. These data streams are an abstraction layer on top of decentralized storage solutions like IPFS or Arweave. One example of a data stream provider is Ceramic.

### Data Schemas <a href="#data-schemas" id="data-schemas"></a>

The data stored in data streams follow a certain structure. This structure (known as a schema) can be pre-published and then the data streams are created in a way that the data stored in them must adhere to this schema.

### Zero-knowledge proofs <a href="#zero-knowledge-proofs" id="zero-knowledge-proofs"></a>

Zero-knowledge Proof (ZKP) is a technique to define whether the provided data is true without revealing it. Simply put, it is a method by which one party can prove to another party that something is true. And they do so without revealing any information apart from the fact that this specific statement is true.

The ability to prove something in zero-knowledge is also a part of data sovereignty.

Plurality employs ZKPs to ensure that the information that which web2 accounts are linked to a certain web3 wallet is only revealed if the user wants it. Otherwise, the information that which accounts are linked is completely concealed.
