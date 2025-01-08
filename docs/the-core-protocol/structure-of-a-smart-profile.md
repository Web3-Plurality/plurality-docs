# Structure of a Smart Profile

Plurality provides a framework for generating reusable, customer-owned profiles that adhere to a standard schema. These profiles are self-sovereign, enabling users to own and control their data while allowing developers and protocols to leverage shared schemas for interoperability across platforms.

This document outlines the standards, schemas, and integration processes for creating and using Smart Profiles.

## Primitives

### Schemas

The Smart Profile System is built on a set of schemas published on the [Ceramic Network](https://ceramic.network/). These schemas define the structure and metadata required to create and manage Smart Profiles. The primary schemas include:



### ProfileType Schema

The `ProfileType` schema provides the model definition for various types of profiles that can be created. Developers can define specific profile types such as:

* **Music Profile**
* **Social Profile**
* **Gaming Profile**

Plurality Network offers a collection of generic profile types that can be reused across decentralized applications (dApps) and protocols, promoting interoperability and a shared social graph.



{% tabs %}
{% tab title="Attributes" %}
* **profile\_name**: Name of the profile type.
* **description**: Description of the profile type.
* **version**: Version of the schema.
* **platforms**: Platforms configured to extract user data (e.g., Facebook, Twitter, Lens, Farcaster).
{% endtab %}

{% tab title="JSON Schema" %}


```
{
  "name": "ProfileTypeV1",
  "schema": {
    "type": "object",
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "properties": {
      "version": {
        "type": "string"
      },
      "platforms": {
        "type": "string"
      },
      "description": {
        "type": "string"
      },
      "profile_name": {
        "type": "string"
      }
    },
    "additionalProperties": false
  },
  "version": "2.0",
  "interface": false,
  "implements": [],
  "accountRelation": {
    "type": "list"
  },
  "immutableFields": []
}
```
{% endtab %}
{% endtabs %}

#### Usage Scenarios:

* **Generic Profile Types**: Developers can use pre-defined profile types published by Plurality Network.
* **Custom Profile Types**: Developers can publish their own profile types tailored to specific use cases, such as a `Sony Profile` for use across Sony’s ecosystem of apps and devices.

### Smart Profile Schema

The SmartProfile schema serves as the foundation for creating user profiles based on a selected ProfileType. These profiles are dynamic, self-sovereign, and interoperable across multiple platforms.

A smart profile schema looks like the following:\


{% tabs %}
{% tab title="Properties" %}
* **username**: The pseudonymous name of the user.&#x20;
* **bio**: A short biography of the user.&#x20;
* **avatar**: The profile picture or avatar associated with the user.&#x20;
* **scores**: A collection of scores such as "reputation score" (calculated from activities on connected platforms) and "social score" (calculated based on connected accounts).&#x20;
* **connectedPlatforms**: A subset of platforms the user has connected to via OAuth, crucial for personality analysis. For example, a social profile type might include Facebook, Twitter, Lens, and Farcaster, but the corresponding SmartProfile might only show Facebook and Twitter if the user connects these platforms.&#x20;
* **profileTypeStreamId**: The unique ID of the `ProfileType` this SmartProfile belongs to.&#x20;
* **version**: The schema version of the SmartProfile.&#x20;
* **extendedPublicData**: A public field where developers can add JSON strings visible to everyone. SDK methods are provided to manage this data.&#x20;
  * **Note**: Sensitive data should be stored in extendedPrivateData instead.
* **privateData**: Encrypted private data secured by Lit Protocol. This field contains:
  * **attestedCred**: Credentials generated during onboarding, such as interests, reputation, badges, and collections, derived using OAuth and AI insights.
  * **attestedPlatformIds**: Unique user IDs or usernames across connected platforms.
  * **linkedAddress:** Blockchain addresses associated with their corresponding chains. This information is private and used to fetch user on-chain traces (e.g., POAPs, NFTs) but remains non-attested for correlation protection.
  * **extendedPrivateData:** Developer-defined JSON strings specific to the application. This data is visible only with user consent and supports functionalities like storing bookmarks or user notes, which are outside the Smart Profile schema.
{% endtab %}

{% tab title="JSON Schema" %}
```json
{
  "name": "smart_profile_v2",
  "schema": {
    "type": "object",
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "properties": {
      "bio": {
        "type": "string"
      },
      "avatar": {
        "type": "string"
      },
      "scores": {
        "type": "string"
      },
      "version": {
        "type": "string"
      },
      "username": {
        "type": "string"
      },
      "attestation": {
        "type": "string"
      },
      "privateData": {
        "type": "string"
      },
      "connectedPlatforms": {
        "type": "string"
      },
      "extendedPublicData": {
        "type": "string"
      },
      "profileTypeStreamId": {
        "type": "string"
      }
    },
    "additionalProperties": false
  },
  "version": "2.0",
  "interface": false,
  "implements": [],
  "accountRelation": {
    "type": "list"
  },
  "immutableFields": []
}
```


{% endtab %}
{% endtabs %}

\


<figure><img src="../.gitbook/assets/image (1) (3).png" alt=""><figcaption><p>Smart Profile structure</p></figcaption></figure>

The model can be seen deployed [here](https://cerscan.com/mainnet/stream/kjzl6hvfrbw6caj1gm7ttjyelgavvi8x278am9ukmbl5mkhyqa3o80y7vzv5iuk)&#x20;

##
