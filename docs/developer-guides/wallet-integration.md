# Wallet Integration

> This guide shows you how to integrate the smart profiles wallet into your application.

Plurality provides an embedded profiles widget that can be integrated into your application to be used as the wallet login solution that supports creation of profiles as well. \
\
Adding the widget is very simple. Let’s take a look at the steps below:&#x20;

### Prerequisites

* Node.js and npm installed
* React v18
* Typescript

### Create or Clone a React Application

Create a react or vite application. You can also clone the boilerplate code from [here](https://github.com/Web3-Plurality/plurality-developer-guides).

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

The PluralitySocialConnect tag adds a login button on your page. When the user clicks on the button it opens the embedded widget which walks the user through the onboarding flow. &#x20;

You can add customized options when adding the SocialConnect tag. There are two fields available in options:

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

* Show your own application's logo (whitelabelling)&#x20;
* Decide which platforms you need to get connected to the profile e.g. TikTok, X, instagram etc.
* Add your own description and custom messaging to help users better onboard to your application



\


