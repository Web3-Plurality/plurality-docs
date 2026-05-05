---
description: >-
  Explore how you can create server side sessions in your application using
  Plurality's SDK
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/5fQAYcOwyn4lTcBwpkV4/developer-guides/embedded-login/server-side-sessions
---

# Server Side Sessions

## What are Sessions?

Sessions are used to uniquely identify users, determine access privileges, and maintain their login state within an application.

When a user signs in through Plurality's social connect widget, a session is created for them on frontend which is used to relieve authenticated users from having to repeatedly login again and again, ensuring a seamless and personalized user experience.

However, what if the application wants to do some authenticated operations for this user using their backend? For e.g. calling some API endpoints or do some access control only for logged in users?

This is where server-side sessions come into play.

> Server-side sessions are a method of storing session data on the server rather than in the client's browser. When a user interacts with a web application, a session is created to maintain state across multiple requests (e.g., logging in, tracking a shopping cart, etc.).

Even though Plurality's widget is primarily a client-side component, however, we offer a comprehensive suite for building dynamic and secure applications and therefore support server-side sessions as well.

## How to create Server Side Sessions with Plurality?

1. Create your app on[ developer dashboard](https://developer.plurality.network/) and extract **Client Id** and **Client Secret** from the dashboard. Your backend should have access to both the Client Id and Client Secret&#x20;

{% hint style="danger" %}
Important: never keep the client secret on the frontend since this is a private secret
{% endhint %}

2. From the frontend, extract the **pluralityToken** by calling the following Plurality SDK function

```typescript
const response = (await PluralitySocialConnect.getLoginInfo()) as ConnectedAccountDataType;
```

This will return the token of the connected user.\
\
3\. Now, to create a session for this user on the backend, send this token from frontend to your backend. In the backend, validate this token by calling the following API. You have to pass in the token in the data, and the clientId and clientSecret in the authorization.

{% hint style="success" %}
You can also use the [swagger](https://app.plurality.network/api/docs-client/#/) here. \
\
1\. Authorize the user by adding `username = clientId` and `password=clientSecret.` 2. Call the /user/validate function giving the `"token": "xxx-token-from-getLoginInfo"` in body.
{% endhint %}

{% tabs %}
{% tab title="cURL" %}
```javascript
curl --location --request GET 'https://app.plurality.network/api/user/validate' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic $(echo -n 'Your-Client-Id:Your-Client-Secret' | base64)' \
--data '{"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImNkODY4MjFlLTRiMDMtNGU3ZS04ZDg5LTRiNzZmZjNmZmU0OSIsInVuaXF1ZVNlc3Npb25JZCI6ImU5M2I0ZDQ1LTg0ZDAtNDRhOS05YzU1LTgyZTgxNjkxZDk3MSIsImlhdCI6MTczOTYyMzU0NCwiZXhwIjoxNzM5NzA5OTQ0fQ.HhMdOI-8vNVGmClrHJuMasfcOdJFaQ-VgxsH4zlgDug"}'
```
{% endtab %}

{% tab title="NodeJS" %}
```typescript
const axios = require('axios');
let data = JSON.stringify({
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImNkODY4MjFlLTRiMDMtNGU3ZS04ZDg5LTRiNzZmZjNmZmU0OSIsInVuaXF1ZVNlc3Npb25JZCI6ImU5M2I0ZDQ1LTg0ZDAtNDRhOS05YzU1LTgyZTgxNjkxZDk3MSIsImlhdCI6MTczOTYyMzU0NCwiZXhwIjoxNzM5NzA5OTQ0fQ.HhMdOI-8vNVGmClrHJuMasfcOdJFaQ-VgxsH4zlgDug"
});

const clientId = 'your_client_id';
const clientSecret = 'your_client_secret';

const auth = Buffer.from(`${clientId}:${clientSecret}`).toString('base64');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://app.plurality.network/api/user/validate',
  headers: { 
    'Content-Type': 'application/json', 
    'Authorization': `Basic ${auth}`
  },
  data : data
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});
```


{% endtab %}
{% endtabs %}

If the API returns a valid response, this means that the token is not yet expired and is valid. Based on this response, the application developer can setup a session management scheme on their backend that fits their needs.

{% hint style="info" %}
Have more questions? Get in touch with the team through our [discord](https://discord.com/invite/Mb6ZDgGjcP) to clarify your concerns.
{% endhint %}

