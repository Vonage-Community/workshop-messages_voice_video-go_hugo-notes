---
title: "Vonage App"
weight: 4
---

In this section, you will set up a Vonage application to use with your app.

## 1. New Vonage Application

From the [Dashboard](https://dashboard.nexmo.com), visit "Applications" and then ["Create a new application"](https://dashboard.nexmo.com/applications/new).

Give your new application a name and choose "Generate public and private key"; your browser will download the private key. Please ensure that you save it as a file named **private.key** inside your project folder.

Do not set any capabilities for your application yet - you will add those in the following sections as required.

![New Application](/intro/app_new.png)

## 2. Link your Vonage Number

Once you have created the application, from the list of available numbers, link the Vonage number you rented earlier, to use with this app. Multiple numbers can be linked.

![App Numbers](/intro/app_numbers.png)

## 3. Environment Variables

Open your app into your favourite code editor or IDE and, in **.env**, add your values for **API_KEY**, **API_SECRET**, **APP_ID** and **VONAGE_NUMBER**.

NB: The value for **PRIVATE_KEY** doesn't need changing as it refer to the local **private.key** filepath.

Please make sure to stop and restart the app:

```sh
nodemon -e js,mustache server.js
```

## Resources

- Vonage Dashboard: [dashboard.nexmo.com](https://dashboard.nexmo.com)
- Vonage Developer Portal: [developer.vonage.com](https://developer.vonage.com)
