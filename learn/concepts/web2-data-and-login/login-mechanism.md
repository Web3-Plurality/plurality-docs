# Login Mechanism

## OAuth

Every user online has created various profiles on different platforms. On these profiles, data against the user is also stored.&#x20;

However, on some platforms, you might see the option of signing in via other social profiles, e.g. sign in with Google or sign in with Facebook. This is done via the open auth (OAuth) tech stack.&#x20;

> OAuth is an open standard for access delegation, commonly used as a way for internet users to grant websites or applications access to their information on other websites but without giving them the passwords.

OAuth can be used to get some basic information about a user from their profile if the user signs in using that account. To get access to more information about the user, in some cases, it is possible to request for an `Access Token` using which more user information can be requested. Explicit user consent is required to get this information.

Plurality uses oAuth and access tokens to fetch the user’s basic profile and other data.
