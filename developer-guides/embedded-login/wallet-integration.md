---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/5fQAYcOwyn4lTcBwpkV4/developer-guides/embedded-login/wallet-integration
---

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

Create a react, vite or next application.&#x20;

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
const options = { clientId: '', theme: 'light', text: 'Customizable Text' };


// in the tsx/jsx part of the page add the following tag
<PluralitySocialConnect
    options={options}
    onDataReturned={handleDataReturned}
/>
```

The PluralitySocialConnect tag adds a "Connect Profile" button on your page. When the user clicks on the button it opens the embedded widget which walks the user through the onboarding flow.<br>

{% hint style="info" %}
Most app developers prefer to create a header component and put the PluralitySocialConnect tag in there. This makes the button consistent across all pages in the website. Once the login process is complete, the button automatically changes to a circular profile icon with the user's avatar.
{% endhint %}

### Create ClientId from Developer Dashboard

Every application that uses Plurality's Social Connect widget needs to provide a clientId created specifically for this application. To get the id, follow the steps:

1. Go to [developer dashboard](https://developer.plurality.network/)
2. Register or Login with your email
3. Fill out the details of your project and create a new application from the dashboard once you are logged in
4. Provide all the details of the application you are building including logo, urls for testing and prod, profile name and description etc.&#x20;
5. Once you press submit, your app will be created and you will be shown three parameters: Client App Id, Client App Secret, and Profile stream Id
6. Copy the client app id and use in the options to embed the plurality social connect in your application.

Explaining the parameters we get from the dashboard a bit more here:

**Client App Id** is the specific public id created for your application which you need to pass in the options for plurality social connect widget. It is a public parameter that needs to be added in your frontend code.

**Client App Secret** is the secret parameter you can use to create server side sessions. More details about it can be read [here](server-side-sessions.md).

**Profile Stream Id** is the stream id created for your app-specific profile created on decentralized storage. You can use that stream to view your published profile on [explorer](https://cerscan.com/mainnet/project/plurality)

{% hint style="info" %}
If your client app secret is compromised, you can rotate it and create a new one from the dashboard. The client app id and profile stream id however are public variables and are fixed.
{% endhint %}

Other than the clientId, you can also pass in theme (which can be either light or dark) and text (which changes the text of the login button).

The code would look like this after adding all parameters of options:

```typescript
import { PluralitySocialConnect } from '@plurality-network/smart-profile-wallet'

const options = { clientId: '6ea8bf02-ea37-403f-b74c-f117fd3bc0a1', theme: 'light', text: 'Customizable Text' };

<PluralitySocialConnect
    options={options}
    onDataReturned={handleDataReturned}
/>
```

### Change Appearance of the Connect Profile Button

If you want to change the appearance of the "Connect Profile" button, you can pass in some UI customization parameters to match the appearance of your platform. Like the following:&#x20;

```typescript
<PluralitySocialConnect
    options={options}
    customization={{
        backgroundColor: 'cyan',
        color: 'black'
    }} 
/>
```

The customization is optional and if you don't want it you can skip it. The following customization options are available though:

<details>

<summary>Button UI Customization Options</summary>

```typescript
customization?: {
    minWidth?: string
    height?: string
    borderRadius?: string
    backgroundColor?: string
    color?: string
    hoverBackgroundColor?: string
    hoverTextColor?: string
    marginTop?: string,
    fontSize?: string,
    fontFamily?: string
};
```

</details>

{% hint style="info" %}
The Smart Profiles Wallet supports all EVM compatible chains but for now, the widget is in beta and by default will use Sepolia Testnet so you can test out the functions in a developer mode.
{% endhint %}

{% hint style="info" %}
Need support for a certain blockchain? Contact us on our [discord](https://discord.com/invite/Mb6ZDgGjcP)&#x20;
{% endhint %}
