---
title: "Vonage App Setup"
weight: 1
---

When you created your Vonage application, no capabilities were selected.

## App Capabilities >> Messages

Navigate to your application and click the **Edit** button.

![App summary](/messages/app.png)

Under **Capabilities**, toggle the switch besides **Messages**. This will enable the use of the Messages API with your app and setting 2 URL to be used as webhooks.

If you use ngrok or localtunnel, enter your given URL followed by the respective paths:

- **https://subdomain.ngrok.io/messages/inbound** - for Inbound URL
- **https://subdomain.ngrok.io/messages/status** - for Status URL

### If you are not able to run any of the tools above, please use:

- `https://edc-2022.ngrok.io/messages/inbound` - for Inbound URL
- `https://edc-2022.ngrok.io/messages/status` - for Status URL

![App Capabilities >> Messages](/messages/app_capabilities.png)

Don't forget to press **Save changes**.

## Status URL

Here what happens when you send a message via the Messages API:

![Sending an SMS](/messages/status_url.gif?classes=thumbnail)

## Inbound URL

Here what happens when you receive a message via the Messages API:

![Receiving an SMS](/messages/inbound_url.gif?classes=thumbnail)
