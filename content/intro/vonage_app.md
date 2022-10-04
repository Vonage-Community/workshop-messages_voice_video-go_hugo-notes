---
title: "Vonage App"
weight: 4
---

In this section, you will set up a Vonage application to use with your app.

## 1. New Vonage Application

From the [dashboard](https://dashboard.nexmo.com), visit "Applications" and then ["Create a new application"](https://dashboard.nexmo.com/applications/new).

Give your new application a name and choose "Generate public and private key"; your browser will download the private key - save it inside your `workshop` project folder.

Set your application to have both Voice and Messaging capabilities - for the webhoos, we will be using the localtunnel URL we create at the previous step, with different paths for each endpoint:

- Voice
  - Answer URL: POST https://subdomain.loca.lt/voice/answer
  - Event URL: POST https://subdomain.loca.lt/voice/events
  - Fallback URL: POST https://subdomain.loca.lt/voice/fallback
- Messages
  - Inbound URL: POST https://subdomain.loca.lt/messages/inbound
  - Status URL: POST https://subdomain.loca.lt/messages/status

![App Capabilities Webhooks](/intro/app_capabilities.png)

Click "Generate new application."

> NB: If you restart your localtunnel and your subdomain is not available anylonger, you will have to update the webhooks to use the new random subdomain you'll be given.

## 2. Link your Vonage Number

Once you have created the application, from the list of available numbers, link the Vonage number you rented earlier, to use with this app. Multiple numbers can be linked.

![App Numbers](/intro/app_numbers.png)

## 3. Environment Variables

Your application will be identified inside Vonage by it's Application ID. Add it as a variable inside the environment file `.env`, together with the `SUBDOMAIN`, `API_KEY`, `API_SECRET`, `VONAGE_NUMBER` and `PRIVATE_KEY`:

```yml
SUBDOMAIN='' # The subdomain you want to use for the server
API_KEY='' # Your Vonage API key
API_SECRET='' # Your Vonage API secret
VONAGE_NUMBER='' # Your Vonage number
APP_ID='' # Your Vonage Application ID
PRIVATE_KEY='-----BEGIN PRIVATE KEY-----
  the contents of private.key goes here
-----END PRIVATE KEY-----' # Your Vonage Application private key

```

**Resources**:

- Vonage Dashboard: [dashboard.nexmo.com](https://dashboard.nexmo.com)
- Vonage Developer Portal: [developer.vonage.com](https://developer.vonage.com)
