# Structure of a Smart Profile

A profile schema looks like the following:\
\
TODO: <\<image here>>



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

\
