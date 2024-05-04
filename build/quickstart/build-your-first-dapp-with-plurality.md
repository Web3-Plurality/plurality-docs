# 🏗️ Build your first dApp with plurality

{% hint style="warning" %}
Plurality is currently in beta. Please do not use it in production.
{% endhint %}

We will create our first dApp that uses Plurality using React framework with typescript.



1. Create a react project with Typescript

```bash
npx create-react-app plurality-dapp --template typescript
```

2. Open the folder plurality-dapp in your editor of choice
3. Install the plurality widget using the following command

```bash
npm i plurality-repconnect-widget
```

4. Go to src/ folder and create a new file declaration.d.ts with the following single line (Note: this step would resolve once a new package update with types comes out):

```bash
declare module 'plurality-repconnect-widget';
```

5. Now open App.tsx file and replace the contents with the following code block

```typescript
import PluralityPopupWidget from 'plurality-repconnect-widget';

function App() {
    // Handle the data returned from the widget
    const handleDataReturned = (data: any) => {
        console.log('Received data from widget:', data);
        // Handle the received data in the external webpage
        // ... (perform actions with the received data)
    };

    return (
        <div>
            <PluralityPopupWidget
                options={{ apps: 'facebook,twitter' }}
                onDataReturned={handleDataReturned}
                customization={{ height: '50px', width: '150px'}} //optional
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
