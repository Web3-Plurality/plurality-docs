# Wallet Integration

> This guide shows you how to integrate the smart profiles wallet into your application.

Plurality provides an embedded profiles widget that can be integrated into your application to be used as the wallet login solution that supports creation of profiles as well.&#x20;

The wallet is created through a network of MPC-TSS in the background and the profile is created on decentralized storage, encrypted with the secrets created through the wallet.&#x20;

The widget allows users to have an easy login while ensuring that they maintain full custody over their wallet and data.  \
\
Adding the widget is very simple. Let’s take a look at the steps below:&#x20;

### Prerequisites

* Node.js and npm installed
* React v18
* Typescript

> Need to quickly get started? [Clone our boilerplate](https://github.com/Web3-Plurality/plurality-developer-guides) to have a basic application with embedded widget and all the wallet functions already in there.

### Create or Clone a React Application

Create a react or vite application.&#x20;

{% hint style="info" %}
The recent react 19 has some breaking changes. If you face these, try downgrading the version of react and react-dom to ^18.0.0 in the package.json
{% endhint %}

### Install Required NPM Packages

Install the following packages

```cmake
npm install @plurality-network/smart-profile-wallet 
```

### Add the Widget to the required page

On the page where you want to create the login/onboarding process, add the following code. You can also simply put it in App.tsx

```typescript
// import the packages at the top of the page
import { PluralitySocialConnect } from '@plurality-network/smart-profile-wallet'


// in the ts part of the page add the following
const options = { cliendId: '', theme: 'light' };


// in the tsx/jsx part of the page add the following tag
<PluralitySocialConnect
    options={options}
    onDataReturned={handleDataReturned}
/>
```

The PluralitySocialConnect tag adds a "Connect Profile" button on your page. When the user clicks on the button it opens the embedded widget which walks the user through the onboarding flow.\


{% hint style="info" %}
Most app developers prefer to create a header component and put the PluralitySocialConnect tag in there. This makes the button consistent across all pages in the website. Once the login process is complete, the button automatically changes to a circular profile icon with the user's avatar.
{% endhint %}

You can add customized options when adding the PluralitySocialConnect tag. There are two fields available in options:

1. **ClientId** is the specific id created for your application based on the customizations you have provided. If you keep it empty it will just give you the default widget.&#x20;
2. **Theme** has two options: dark and light. The dark option is partially implemented for now and will be completely implemented soon.

If you keep clientId as empty, then it will just pick up default settings. For testing purposes, this is okay. But for customizing the widget according to your needs and making your application production ready, you must get your own clientId from us.&#x20;

### Customize the widget according to your needs

The embedded widget is highly customizable and supports not only dynamic options, but also branding specific to your application. To customize the widget, you need to do the following steps:

1. Fill out [this form](https://forms.gle/Rw54YZFZjUR3fkXV7) which will ask for your preferences.
2. Wait 1-2 business days, our team will do the entire setup for you in the backend and send you an email with your clientId. Please note that this step will get automated over the course of next few months when we launch our developer dashboard.
3. Once you get your clientId, add it into the options of the PluralitySocialConnect tag.&#x20;

**So, what can you customize?**

You can customize the widget to:

* Show your own application's logo (white labelling)&#x20;
* Decide which platforms you need to get connected to the profile e.g. TikTok, X, instagram etc.
* Add your own description and custom messaging to help users better onboard to your application

### Supported Platforms

You can connect the following platforms in your user's profile:

* Facebook
* Instagram
* X
* TikTok
* Roblox
* Fortnite
* Snapchat

### Supported Chains

The Smart Profiles Wallet supports all EVM compatible chains for now. Support for non-evm chains will be added in the future.

{% hint style="info" %}
Need support for a certain blockchain? Contact us on our [discord](https://discord.com/invite/Mb6ZDgGjcP)&#x20;
{% endhint %}
