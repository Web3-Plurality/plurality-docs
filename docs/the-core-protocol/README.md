---
icon: atom-simple
---

# The Core Protocol

The core protocol has various facets. Let’s clarify the key modules one by one on a technical level.&#x20;

We have been talking about a Smart Profile quite a lot, but what exactly is it and how is it created?

## What is a Smart Profile?

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdz1IyHw_P7vukjIG71MDSHs7cGZlnVgWzGErFFdyzLG6b8pLySkvf-xRr2isUNlw-dae-heTRLW97At8knNOSWeEr65G0-AjpdgxipO39at359PlhKSHAO95zDUnnsfliUyuHO96v1oG1jjsN3Z8TR0vI?key=8Tn-B_kMRBjpwlED5ztQaw" alt=""><figcaption><p>Aggregated Context from Web2 and Web3 Platforms</p></figcaption></figure>



Smart Profiles are data backpacks that get aggregated from user’s existing profiles and addresses. The data is processed via AI models to extract meaningful insights.&#x20;

Every wallet can have n profiles connected to them representing the different contexts of a person’s digital life.&#x20;

Each profile can source data from n different sources again based on context. To understand the workflow better, let’s follow the journey of Alice and how she can create and use Smart Profiles.&#x20;

### Alice creates Smart Profiles

Alice is an engineer who likes to listen to music, read news, watch movies and play games.&#x20;

For each of the different personas she has in her life, she utilizes different profiles.\
\
For her work related activities, she posts on LinkedIn and pushes commits on Github. For her entertainment, she uses YouTube, Spotify, Netflix. For her social life, she uses Instagram, Farcaster, Lens. And she also has multiple addresses on multiple blockchains where she uses different platforms like Polymarket, Zora.&#x20;

However, all of these profiles are siloed and not interoperable. Alice can create smart profiles from her existing digital footprint which she can take with her anywhere on any platform. An example attribution of her Smart Profiles could be like this

{% tabs %}
{% tab title="Social Profile" %}
Data aggregated from Instagram, X, Farcaster, Lens
{% endtab %}

{% tab title="Music Profile" %}
Data aggregated from YouTube, Spotify, Music NFT Platforms
{% endtab %}

{% tab title="Work Profile" %}
Data aggregated from LinkedIn, GitHub
{% endtab %}
{% endtabs %}

Once Alice creates these profiles, they get cryptographically linked to her chain-agnostic wallet that she can then use on any platform on any blockchain.&#x20;

Now that you have a basic understanding of how Smart Profiles are created and used, we can go into further technical details of the steps involved.

## Steps of creating a Smart Profile

{% stepper %}
{% step %}
### Wallet Creation

The first step before any decentralized profile is created is figuring out the root keys that get tagged with a Smart Profile to make them interoperable.&#x20;

Plurality Network comprises a Multi-Party Compute (MPC) wallet solution that allows user to easily create multi-chain wallets “invisibly” using their email or social logins while making sure that user has complete custody over their wallets. No more thinking about seed phrases or thinking about how to download a wallet and separate wallets for separate chains.&#x20;

A root wallet is created for the user invisibly in the background the first time they login through their email or socials (whichever they choose). The smart profile gets tagged to this wallet. &#x20;
{% endstep %}

{% step %}
### Data Aggregation

Smart Profiles are different from traditional profiles in the way that they are not created empty - rather they source data from the user's existing digital footprint and use it to pre-populate the profile when it’s first created. After creation, user’s actions on various platforms contribute further to the enrichment of the profile.&#x20;

This data can be sourced from web2 or web3 platforms.&#x20;

**Web2 Data Aggregation**

From web2 platforms, we utilize OAuth protocol to gather data that is collected against a user's profile by the platform. OAuth protocol only allows access to certain data if the user logs into their profile and allows access. We are creating this protocol to uphold user consent, that is why we do not use any method of data sourcing other than oauth which ensures that data is extracted after the user’s consent.\
\
**Web3 Data Aggregation**

For web3 data gathering, we have indexer nodes that index blockchain data. Users will need to connect their blockchain addresses with their profiles for the data to be sourced. Again, this doesn’t happen until the user explicitly connects their address to their smart profile.
{% endstep %}

{% step %}
### AI Processing

Once the data is aggregated, it's all coming from disparate sources in non-normalized forms. For the data to make sense, it needs to be sanitized, processed and converted to a standardized form that could be consumed later on.&#x20;

For this, we have AI agents that do the processing in a private way. After processing, only the processed data is stored in the profile. The raw data is thrown away and never stored anywhere.&#x20;
{% endstep %}

{% step %}
### Profile Data Encryption

Once the profile data is created, it then gets encrypted with the Decentralized Identifiers (DIDs) created against the wallet address of the user.
{% endstep %}

{% step %}
### Profile Attestation

In order for the correct functioning of the entire system, it is important that the data in Smart Profiles is verifiable and attested.\
Attestation means that a piece of data is verified by a trusted entity to be true and is not tampered with.&#x20;

Plurality uses Ethereum Attestation Service (EAS) to attest the profile data once it is sanitized and processed.&#x20;
{% endstep %}

{% step %}
### Storage

Encrypted Profiles finally get stored in DID based streams on decentralized storage and can only be decrypted once the user permits.
{% endstep %}
{% endstepper %}

\
\
