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

{% tab title="Example Object" %}
```json
{
  "smartProfile": {
    "username": "cormier",
    "avatar": "https://res.cloudinary.com/dblrsf3fe/image/upload/v1721919290/wkaejhi7ocnwhfl42vb8.png",
    "bio": "",
    "scores": [
      {
        "scoreType": "reputation_score",
        "scoreValue": 0
      },
      {
        "scoreType": "social_score",
        "scoreValue": 3500
      }
    ],
    "connectedPlatforms": [
      "tiktok",
      "snapchat",
      "roblox",
      "fortnite"
    ],
    "profileTypeStreamId": "kjzl6kcym7w8y5e4o0467pkvp693wogi90amrj8gzfr77k7tcngdzm4qrliz50m",
    "version": "2",
    "extendedPublicData": {
      "name": "plural-abc"
    },
    "attestation": {
      "version": 2,
      "uid": "0x57e5893197e3ee0c1c91804cf89f9853fe1efa401b0c9883f03654a9ca36fbc1",
      "domain": {
        "name": "EAS Attestation",
        "version": "0.26",
        "chainId": "11155111",
        "verifyingContract": "0xC2679fBD37d54388Ce493F1DB75320D236e1815e"
      },
      "primaryType": "Attest",
      "message": {
        "version": 2,
        "recipient": "0x1DfcA5Aa1F5962D65a26Ea3Fa4FaB23ACe4c47C9",
        "expirationTime": "0",
        "time": "1736674391",
        "revocable": false,
        "schema": "0x7fd459e85a1d718e1ffd9869505b0ad015ff6a4fe6fcfe12a6020183980b098d",
        "refUID": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "data": "0x00000000000000000000000000000000000000000000000000000000000000e00000000000000000000000000000000000000000000000000000000000000120000000000000000000000000000000000000000000000000000000000000014000000000000000000000000000000000000000000000000000000000000001c0000000000000000000000000000000000000000000000000000000000000024000000000000000000000000000000000000000000000000000000000000002a000000000000000000000000000000000000000000000000000000000000003000000000000000000000000000000000000000000000000000000000000000007636f726d696572000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000005668747470733a2f2f7265732e636c6f7564696e6172792e636f6d2f64626c7273663366652f696d6167652f75706c6f61642f76313732313931393239302f776b61656a6869376f636e7768666c34327662382e706e670000000000000000000000000000000000000000000000000000000000000000000000000000000000605b7b2273636f726554797065223a2272657075746174696f6e5f73636f7265222c2273636f726556616c7565223a307d2c7b2273636f726554797065223a22736f6369616c5f73636f7265222c2273636f726556616c7565223a333530307d5d00000000000000000000000000000000000000000000000000000000000000295b2274696b746f6b222c22736e617063686174222c22726f626c6f78222c22666f72746e697465225d0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000003f6b6a7a6c366b63796d377738793565346f30343637706b7670363933776f67693930616d726a38677a667237376b3774636e67647a6d3471726c697a35306d0000000000000000000000000000000000000000000000000000000000000000032232220000000000000000000000000000000000000000000000000000000000",
        "salt": "0xbe2060bc76299155ef6e48f5bd2a6b493f1b117df1fef6bb2dca593d9d49b843"
      },
      "types": {
        "Attest": [
          {
            "name": "version",
            "type": "uint16"
          },
          {
            "name": "schema",
            "type": "bytes32"
          },
          {
            "name": "recipient",
            "type": "address"
          },
          {
            "name": "time",
            "type": "uint64"
          },
          {
            "name": "expirationTime",
            "type": "uint64"
          },
          {
            "name": "revocable",
            "type": "bool"
          },
          {
            "name": "refUID",
            "type": "bytes32"
          },
          {
            "name": "data",
            "type": "bytes"
          },
          {
            "name": "salt",
            "type": "bytes32"
          }
        ]
      },
      "signature": {
        "v": 27,
        "r": "0xfbc954fbdc9b73d26e193ae34349a6e27e80649501ae715f9a3b2b9af44c3595",
        "s": "0x1ce8de0c36a44264a90242578bf5d8bccc2192dbd0b0cd09661c37ce324e67e8"
      }
    },
    "privateData": {
      "attestedCred": {
        "interests": [
          "Engineering",
          "TikTok",
          "Political Memes",
          "playing cricket",
          "farm",
          "fighting games",
          "engineering",
          "gaming",
          "professional gaming"
        ],
        "reputationTags": [
          "Engineer",
          "engineer",
          "professional gamer"
        ],
        "badges": [],
        "collections": [
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0xMTI1ODk5OTA2ODQzMTY5",
            "assetDetails": {
              "assetId": "1028595",
              "inventoryItemAssetType": "CLASSIC_TSHIRT",
              "instanceId": "1125899906843169"
            }
          },
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0xMTI1ODk5OTA2ODQzMTcw",
            "assetDetails": {
              "assetId": "1772336109",
              "inventoryItemAssetType": "HAT",
              "instanceId": "1125899906843170"
            }
          },
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0yMzQ2MzMyOTUyMTc",
            "assetDetails": {
              "assetId": "102611803",
              "inventoryItemAssetType": "HAT",
              "instanceId": "234633295217"
            }
          },
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0xMTI1ODk5OTA2ODQzMTcx",
            "assetDetails": {
              "assetId": "4047884939",
              "inventoryItemAssetType": "CLASSIC_SHIRT",
              "instanceId": "1125899906843171"
            }
          },
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0xMTI1ODk5OTA2ODQzMTcy",
            "assetDetails": {
              "assetId": "382537702",
              "inventoryItemAssetType": "CLASSIC_SHIRT",
              "instanceId": "1125899906843172"
            }
          },
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0xMTI1ODk5OTA2ODQzMTcz",
            "assetDetails": {
              "assetId": "382537085",
              "inventoryItemAssetType": "CLASSIC_SHIRT",
              "instanceId": "1125899906843173"
            }
          },
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0xMTI1ODk5OTA2ODQzMTc0",
            "assetDetails": {
              "assetId": "144076436",
              "inventoryItemAssetType": "CLASSIC_SHIRT",
              "instanceId": "1125899906843174"
            }
          },
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0xMTI1ODk5OTA2ODQzMTc1",
            "assetDetails": {
              "assetId": "382538059",
              "inventoryItemAssetType": "CLASSIC_SHIRT",
              "instanceId": "1125899906843175"
            }
          },
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0xMTI1ODk5OTA2ODQzMTc2",
            "assetDetails": {
              "assetId": "382538295",
              "inventoryItemAssetType": "CLASSIC_SHIRT",
              "instanceId": "1125899906843176"
            }
          },
          {
            "path": "users/6180306719/inventory-items/VVNFUl9BU1NFVF9JRD0xMTI1ODk5OTA2ODQzMTc3",
            "assetDetails": {
              "assetId": "382537806",
              "inventoryItemAssetType": "CLASSIC_PANTS",
              "instanceId": "1125899906843177"
            }
          }
        ],
        "attestation": {
          "version": 2,
          "uid": "0x5a0b3e797f1f12e814c56d257b9a8c0a9ba99f9dd360aa77c3ad47f758519762",
          "domain": {
            "name": "EAS Attestation",
            "version": "0.26",
            "chainId": "11155111",
            "verifyingContract": "0xC2679fBD37d54388Ce493F1DB75320D236e1815e"
          },
          "primaryType": "Attest",
          "message": {
            "version": 2,
            "recipient": "0x1DfcA5Aa1F5962D65a26Ea3Fa4FaB23ACe4c47C9",
            "expirationTime": "0",
            "time": "1736674392",
            "revocable": false,
            "schema": "0x20351f973fdec1478924c89dfa533d8f872defa108d9c3c6512267d7e7e5dbc2",
            "refUID": "0x0000000000000000000000000000000000000000000000000000000000000000",
            "data": "0xc011c268a2f201ab78c46eac9d18209c37ef0ed86cd91125fcb5a71db8043ea4",
            "salt": "0xc0df5e1cd050bf7e08e87f211b67287f1db53993108c2700f93526fe40195cd6"
          },
          "types": {
            "Attest": [
              {
                "name": "version",
                "type": "uint16"
              },
              {
                "name": "schema",
                "type": "bytes32"
              },
              {
                "name": "recipient",
                "type": "address"
              },
              {
                "name": "time",
                "type": "uint64"
              },
              {
                "name": "expirationTime",
                "type": "uint64"
              },
              {
                "name": "revocable",
                "type": "bool"
              },
              {
                "name": "refUID",
                "type": "bytes32"
              },
              {
                "name": "data",
                "type": "bytes"
              },
              {
                "name": "salt",
                "type": "bytes32"
              }
            ]
          },
          "signature": {
            "v": 27,
            "r": "0xf16c1598a1fd13a2e15dfa25a71d06e36cefc0a680ca5c8c246b1c802815cc15",
            "s": "0x699d089d773bdc4ae6abd53650eba8ba27c310844c6fc1ca235cb3fc80856b1f"
          }
        },
        "salt": {
          "interests": "0x2ed160b984b57c0969e343daf341eaae56b61b4e91d8a96e7b6f62591bbb6136",
          "reputationTags": "0xac93ea7dc083465a471afb1aed84237ff677753a172a76354a8c9045650f5383",
          "badges": "0xde2afbcce5949cb9dd87537fe80fa7d5eb10db5719feb00c5566679cd54ad78b",
          "collections": "0x160b2c9a59e3fa0be295afa360dacb6cdb8a578686e88eef3c5edf7e3f4530a6"
        }
      },
      "attestedPlatformIds": {
        "connectedProfiles": [
          {
            "platformType": "tiktok",
            "userPlatformId": "",
            "username": "web3plurality"
          },
          {
            "platformType": "snapchat",
            "userPlatformId": "CAESICwQSJKRj2tZcfwPoHgyeBtqLtgX9x1IiouZGsNUWzQn",
            "username": "Plurality"
          },
          {
            "platformType": "roblox",
            "userPlatformId": "",
            "username": "Plurality"
          },
          {
            "platformType": "fortnite",
            "userPlatformId": "7fa71fce64974c9580a824c345e78ca5",
            "username": "plurality3"
          }
        ],
        "attestation": {
          "version": 2,
          "uid": "0x8753ed3087961613f1a751ab55a7a52b11390fe9f92e5142c789cb74fdf9bd6f",
          "domain": {
            "name": "EAS Attestation",
            "version": "0.26",
            "chainId": "11155111",
            "verifyingContract": "0xC2679fBD37d54388Ce493F1DB75320D236e1815e"
          },
          "primaryType": "Attest",
          "message": {
            "version": 2,
            "recipient": "0x1DfcA5Aa1F5962D65a26Ea3Fa4FaB23ACe4c47C9",
            "expirationTime": "0",
            "time": "1736674392",
            "revocable": false,
            "schema": "0x20351f973fdec1478924c89dfa533d8f872defa108d9c3c6512267d7e7e5dbc2",
            "refUID": "0x0000000000000000000000000000000000000000000000000000000000000000",
            "data": "0xfbf1aca3e563188ffb1ae2015abc4a9ab7ea63f23214aa4348e2145b0c15ccac",
            "salt": "0xc4b072935fc53a5acb43650a7e8ab5b9f2dc4309f56b67d89b3b5656a807bff8"
          },
          "types": {
            "Attest": [
              {
                "name": "version",
                "type": "uint16"
              },
              {
                "name": "schema",
                "type": "bytes32"
              },
              {
                "name": "recipient",
                "type": "address"
              },
              {
                "name": "time",
                "type": "uint64"
              },
              {
                "name": "expirationTime",
                "type": "uint64"
              },
              {
                "name": "revocable",
                "type": "bool"
              },
              {
                "name": "refUID",
                "type": "bytes32"
              },
              {
                "name": "data",
                "type": "bytes"
              },
              {
                "name": "salt",
                "type": "bytes32"
              }
            ]
          },
          "signature": {
            "v": 28,
            "r": "0x74d8bd0326f96ad179bd2b5b03d1a4f6e8b6ac0d14608fd781d91ba8df2ad2b8",
            "s": "0x49f8bb0e26fe81e190406c0b93aada33d60cf276348ae3859aa34251ee061028"
          }
        },
        "salt": {
          "tiktok": "0x8eed15ca262c9dc6af41bdb6629b3df565b254aa85f04268289c5a0a9088eeb0",
          "snapchat": "0x5b4e711f1b83bd4ab1e80f5f75b1789cda9363cc501dc27015455286f2f8bdbe",
          "roblox": "0x0b314945eee305bd9300d40f42924b922d3366685457ac9290a9badebf95a816",
          "fortnite": "0x22b09d8dac87f6d3e05760f5ac8cd3b9086a331914bca870e499b695e9e22ace"
        }
      },
      "linkedAddress": [],
      "extendedPrivateData": {
        "roblox": {
          "placesVisit": "0",
          "friends": "0",
          "followers": "0",
          "following": "0"
        },
        "tiktok": {
          "followerCount": 0,
          "followingCount": 0,
          "videoCount": 0,
          "likesCount": 0
        },
        "work": "Plurality"
      }
    }
  }
}
```


{% endtab %}
{% endtabs %}

\


<figure><img src="../.gitbook/assets/image (1) (3).png" alt=""><figcaption><p>Smart Profile structure</p></figcaption></figure>

The model can be seen deployed [here](https://cerscan.com/mainnet/stream/kjzl6hvfrbw6caj1gm7ttjyelgavvi8x278am9ukmbl5mkhyqa3o80y7vzv5iuk)&#x20;

## Features

### Native OAuth Integration

Plurality Network provides native OAuth-based integrations with over 10 platforms. This allows developers to bootstrap profiles with user data from existing platforms, enabling features like:

* Importing user interests
* Establishing reputation scores
* Calculating social scores

Developers can configure their profile types with a selected list of platforms for data extraction.

List of supported platforms

### Public Data Attestation

An EAS schema defines the public attributes of Smart Profiles for data attestation. These attributes ensure the integrity of user data and include:

* **name**: The pseudonymous name of the user.
* **bio**: A short biography of the user.
* **avatar**: The user’s profile picture.
* **scores**: Collection of various scores, such as reputation and social scores.
* **connectedPlatforms**: List of platforms the user has connected to via OAuth.
* **profileTypeStreamId**: The unique ID of the `ProfileType` the SmartProfile belongs to.
* **version**: Version of the SmartProfile schema.
* **extendedPublicData**: Public JSON data added by developers, visible to everyone. SDK methods allow developers to set or retrieve this information.

### Private Data Attestation

Private attributes of Smart Profiles are encrypted using Lit Protocol and securely stored. Developers can utilize SDK methods to interact with these attributes, ensuring sensitive information is securely stored and accessible only after user consent. This field supports private data attestations for attributes such as:

*   **attestedCred**: Credentials generated during the onboarding process. These include the following schema:

    * `{name: interests, value: interests[], salt, type}`
    * `{name: reputation, value: reputation[], salt, type}`
    * `{name: badges, value: badges[], salt, type}`
    * `{name: collection, value: badges[], salt, type}`
    * `{name: attestationData, value: attestation}`

    These values (e.g., interests, reputation, badges, collections) are extracted during onboarding from the user's existing profiles on connected platforms. OAuth data combined with AI-generated insights form these attributes, which are issued as private attestations using EAS. Users can generate proofs to selectively disclose attributes to external parties as needed.

    **Example**: A user can provide a proof of their `interests` attestation issued by Plurality and share it with a dApp during login for personalized recommendations.
* **attestedPlatformIds**: Unique identifiers or usernames across various platforms linked via OAuth. These credentials enable users to create on-chain or off-chain proofs, such as verifying their Twitter handle.
  * `{name: <platform_type>, value: <username>, salt, type}`
