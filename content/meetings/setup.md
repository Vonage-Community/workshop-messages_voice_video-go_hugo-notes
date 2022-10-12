---
title: "Vonage App Setup"
weight: 1
---

Your Vonage application has currently the Messages & Voice capabilities only - we'll add Meetings to the mix.

## App Capabilities >> Meetings

Navigate to your application and click the **Edit** button.

![App summary](/meetings/app.png)

Under **Capabilities**, toggle the switch besides **Voice**. This will enable the use of the Voice APIs with your app and setting 3 URL to be used as webhooks.

If you using ngrok, enter your given URL followed by the respective paths:

- **https://subdomain.ngrok.io/meetings/rooms** - for Rooms URL
- **https://subdomain.ngrok.io/meetings/sessions** - for Sessions URL

![App Capabilities >> Meetings](/meetings/app_capabilities.png)

Don't forget to press **Save changes**.