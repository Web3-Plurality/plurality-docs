# Login Mechanism

## Traditional Login Mechanism

To get started on a web2 platform, most of them require users to create a profile.&#x20;

To create a profile, users need to fill out some information and then set up a username/email password. Later on, to login to this profile, users need to remember the username & password and use it.

For a few profiles, this worked fine. But later on, as the number of platforms grew, creating new passwords for every platform became a hassle. Moreover, as the data on each platform grew, it made sense to create apps on top of these platforms that could use this data. So the question came forward, is it possible to reuse the profile that was created on one platform to create a profile on another? That's when protocols like OAuth came into being.&#x20;

## Open Auth Protocol (OAuth)

Every user online has created various profiles on different platforms. On these profiles, data against the user is also stored.&#x20;

However, on some platforms, you might see the option of signing in via existing social profiles, e.g. sign in with Google or sign in with Facebook. This reuse of profiles is done via the open auth (OAuth) tech stack.&#x20;

> OAuth is an open standard for access delegation, commonly used as a way for internet users to grant websites or applications access to their information on other websites but without giving them the passwords.

OAuth can be used to get some basic information about a user from their profile if the user signs in using that account.&#x20;

### Access Tokens

Some platforms store a lot more information about the user other than basic profile data. To get access to this extra information about the user, it is sometimes possible to request for a `Access Token` during the OAuth workflow. This access token is a string of hexadecimal characters valid for a little while using which more user information can be extracted.&#x20;

However, explicit user consent is required to get this information to ensure only allowed apps/websites get access to the user's information.
