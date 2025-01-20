# Smart Profiles SDK

> This guide shows how to use the user profile associated with each wallet

**Our embedded widget is more than just a wallet. It is a comprehensive profile solution.** \
\
Each wallet has n different profiles attached to it, one of which is tagged to your application based on the customizations that you did when setting up the widget.&#x20;

{% hint style="info" %}
Ideally each application should setup a profile that is closest to their use case. For e.g. if you are a social application, use the pre-built social profile or if you are a gaming platform, use the gaming profile.&#x20;

This will allow users that have utilized similar platforms to have a one-click onboarding to your platform, making it extremely easy for users to check out your application.&#x20;
{% endhint %}

Each profile contains basic user information like name, bio, avatar and description. Moreover, it also has the user's interests & reputation which are analyzed from the social accounts connected to that profile. Lastly, it also supports scores, some of which are calculated by the protocol, others you can setup for your specific application.&#x20;

{% hint style="info" %}
Support for custom scoring is not yet shipped but will soon. The protocol level scoring however is available which increases the score when more platforms are connected to the profile by the user.
{% endhint %}

## Smart Profiles Schema

The Smart Profiles Schema can be viewed [here](../the-core-protocol/structure-of-a-smart-profile.md).

## Using the Profiles SDK

As an application developer, you can get profile data from the connected wallet. This will allow you to customize your interface according to your user. Also, it will allow you to cater to your user’s interests and tailor experience accordingly.&#x20;

For example, you can offer product recommendations, or curate user’s feed or show them relevant content.&#x20;

You can also gate access to certain content or area of your application based on the profile’s information.

Every time the user does a successful login, you will get a response in the data handler that’s attached to the embedded widget

```typescript
const handleDataReturned = (data) => {
        const receivedData = JSON.parse(JSON.stringify(data))
        console.log(receivedData);
    };


<PluralitySocialConnect
        options={options}
        onDataReturned={handleDataReturned}
/>
```

If login has been successful and there is now a valid session, the handleDataReturned function will get a valid jwt token showing that there is now an active session.&#x20;

{% hint style="info" %}
To view the profiles data, you can visit the [explorer](https://cerscan.com/mainnet/project/plurality)
{% endhint %}

### Get Smart Profile Data

To fetch the smart profile data, you can use the following function.

```typescript
const response = (await PluralitySocialConnect.getSmartProfileData()) as ConnectedAccountDataType;
if (response) {
    const smartProfileData = response.data;
    return smartProfileData;
}
```

### Fetch Login Information

At any point in your application, if you want to fetch the login information of the connected account i.e. the status of the connected and session token (JWT), then you can use the following function.

```typescript
const response = (await PluralitySocialConnect.getLoginInfo()) as ConnectedAccountDataType;
if (response) {
    const loginInfoData = response.data;
    console.log("Connected Account Info (Inisde dApp)::", loginInfoData);
    return loginInfoData;
}
```

### Update User Consent

When the user logs in to the platform the first time, they are asked whether they want to share their data with this platform or not. If the user decides not to share data, then the application only gets basic user information including name, avatar, bio. However, if the user decides to share their information then the application gets all the required data e.g. interests, reputation, scores, etc. \
\
However, user can change their decision anytime throughout the application flow. If at any point throughout the application flow, you want to ask users to reconsider their consent, then the update consent function can be used.&#x20;

```typescript
const response = (await PluralitySocialConnect.updateConsentOption()) as ConnectedAccountDataType;
if (response) {
    const smartProfileData = response.data;
    return smartProfileData;
}
```

## Set Smart Profile Data

As a decentralized application developer, you might also need to store user’s information in a verifiable, decentralized, but gasless and privacy-preserving way. If you want to store any information about the user derived from their actions on your platform, you can set that information in your user’s profile. Next time when the user logs in to you application again, your application will have access to this data again through the SDK functions. \
\
This provides an out-of-the-box profile solution for your application without you having to worry about setting up a database or taking any liability for user data. With Plurality’s SDK, managing user profiles is as simple as calling get and set functions.

#### Visibility and permissions of the stored data

Since user profiles are shared amongst different apps and platforms, if you want to ensure that the data you put in your user’s profile cannot be seen by any other application, then your application needs to set it in a private way.&#x20;

The application has two options:

* **Store data publicly:** Suitable for any data that is not sensitive for the application. It will be available to all other applications as well if they want to read it.
* **Store data privately:** Suitable for sensitive data. It will only be readable for the application that stored it initially. No other application will be able to read it even if they use the same profile schema.&#x20;

### Set Public Data

Applications can store data for handling any business logic on the application publicly.&#x20;

```typescript
const response = (await PluralitySocialConnect.setPublicData("key", "value")) as ConnectedAccountDataType;
if (response) {
    return response.data
}
```

### Get Public Data

To get previously stored data, the application can get it using the following function

```typescript
const response = (await PluralitySocialConnect.getPublicData("key")) as ConnectedAccountDataType;
if (response) {
    console.log("response", response.data)
}
```

### Set Private Data

Applications can store data for handling any business logic on the application privately.&#x20;

```typescript
const response = (await PluralitySocialConnect.setPrivateData("key", "value")) as ConnectedAccountDataType;
if (response) {
    console.log("response", response.data)
}
```

### Get Private Data

To get previously stored data, the application can get it using the following function

```typescript
const response = (await PluralitySocialConnect.getPrivateData("key")) as ConnectedAccountDataType;
if (response) {
    console.log("response", response.data)
}
```
