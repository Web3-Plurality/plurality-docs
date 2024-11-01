# Structure of a Smart Profile

A Smart Profile  schema binds together multiple IndividualProfile schemas, where each individual profile represents the data aggregated and processed from one platform&#x20;

## Smart Profile Schema

A smart profile schema looks like the following:\


{% tabs %}
{% tab title="Properties" %}
* scores :string
* version :string
* connected\_platforms :string
* encrypted\_profile\_data :string
* profile\_type\_stream\_id :string
{% endtab %}

{% tab title="JSON Schema" %}
```json
{
  "name": "SmartProfileV1",
  "schema": {
    "type": "object",
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "properties": {
      "scores": {
        "type": "string"
      },
      "version": {
        "type": "string"
      },
      "connected_platforms": {
        "type": "string"
      },
      "encrypted_profile_data": {
        "type": "string"
      },
      "profile_type_stream_id": {
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

The model can be seen deployed [here](https://cerscan.com/mainnet/stream/kjzl6hvfrbw6c7hdfsos86ep6bnq1hemddmkklxqdjygvla080r285bcpac7tt7)

## Individual Profile Schema

An individual profile schema looks like the following:

{% tabs %}
{% tab title="Properties" %}
* scores :string
* version :string
* platform\_name :string
* encrypted\_profile\_data :string
{% endtab %}

{% tab title="JSON Schema" %}
```json

{
  "name": "IndividualProfileV1",
  "schema": {
    "type": "object",
    "$schema": "https://json-schema.org/draft/2020-12/schema",
    "properties": {
      "scores": {
        "type": "string"
      },
      "version": {
        "type": "string"
      },
      "platform_name": {
        "type": "string"
      },
      "encrypted_profile_data": {
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

The model can be seen deployed [here](https://cerscan.com/mainnet/stream/kjzl6hvfrbw6cb3yohf2est7xb35wo1r3mtshcqz16f7ymhm7mkwi11pgnx9jgl)

A profile consists of some public content and some private content.&#x20;

## Public Profile Content

### Username

The username selected by the user. The protocol auto assigns a gender-neutral username when the profile is first created. But user can change the username after creation at any point.

This username can be reused across platforms.

### Profile Picture

The avatar or profile picture selected by the user. The protocol auto assigns a profile image when the profile is first created. But user can change the profile picture after creation at any point.

This profile picture can be reused across platforms.

### Scores

A list of scores that could be verifiably computed against the user's profile. The protocol profiles some standard scores e.g. reputation and engagement scores. However, the integration application can also setup custom scoring methods based on their specific use case.&#x20;

These scores can also be used for gating access to content or unlocking certain on-chain or off-chain methods.&#x20;

## Private Profile Content

### Interests

The list of user interests in the particular profile’s context. These interests are inferred from user's activity on platforms whose profiles are used to source data for this particular Smart Profile

### Reputation

The list of things the user has a reputation in. These are the topics that user talks about or posts about or the provable skills that the user has demonstrated through their online presence.

### Social Graph

Every profile has an associated interoperable social graph sourced from the network of the profiles that user has connected with this particular smart profile. Moreover, user also has the option of growing the social graph further by connecting to people on-chain as well.
