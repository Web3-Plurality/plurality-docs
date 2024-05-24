---
description: ...
---

# 🏗️ Build your first dApp with plurality

{% hint style="warning" %}
Plurality is currently in beta. Please do not use it in production.
{% endhint %}

We will create our first dApp that uses Plurality using React framework with typescript.

{% hint style="info" %}
Want to jump directly to code? Checkout final code on [Git](https://github.com/Web3-Plurality/demo-application)
{% endhint %}

1. Create a react project with Typescript

```bash
npx create-react-app plurality-dapp --template typescript
```

2. Open the folder plurality-dapp in your editor of choice
3. Install the plurality widget using the following command

```bash
npm i plurality-social-connect
```

4. Go to src/ folder and create a new file declaration.d.ts with the following single line (Note: this step would resolve once a new package update with types comes out):

```bash
declare module 'plurality-social-connect';
```

5. Now open App.tsx file and replace the contents with the following code block

```typescript
import PluralitySocialConnect from 'plurality-social-connect';
import { useRef } from 'react';

const App = () => {
    const childRef: any = useRef(null);
    // Profile data handle
    const handleProfileDataReturned = (data) => {
        const receivedData = JSON.parse(JSON.stringify(data))
        console.log("Get profile data:", receivedData);
        alert(JSON.stringify(data));
        childRef.current.closeSocialConnectPopup();
    };

    return (
        <div>
            <PluralitySocialConnect
                options={{ apps: 'facebook,twitter' }}
                onProfileDataReturned={handleProfileDataReturned}
                // all customization params are optional
                // customization={{ height: '200px', width: '500px', initialBackgroundColor: '#E8A123', initialTextColor: '#FFFFFF', flipBackgroundColor: '#12AE83', flipTextColor: '#FFFFFF'}}
                ref={childRef}
            />
        </div>
    );
};
export default App;
```

6. Now run the demo with the following command

```bash
npm install && npm start
```

You should see a big pink button. Clicking on it will open the widget with the required workflows. If the user completes the workflow, their data will be received in the `handleDataReturned` event function.
