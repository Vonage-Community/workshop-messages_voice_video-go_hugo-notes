---
title: "Vonage App Setup"
weight: 1
---

Your Vonage application has currently the Messages capability only - we'll add Voice to the mix.

## App Capabilities >> Voice

Navigate to your application and click the **Edit** button.

![App summary](/voice/app.png)

Under **Capabilities**, toggle the switch besides **Voice**. This will enable the use of the Voice APIs with your app and setting 3 URL to be used as webhooks.

![App edit](/voice/app_capabilities.png?classes=thumbnail_lg)

If you use ngrok or localtunnel, enter your given URL followed by the respective paths, changing the HTTP method to **HTTP POST**:

- **POST: https://subdomain.ngrok.io/voice/answer** - for Answer URL
- **POST: https://subdomain.ngrok.io/voice/event** - for Event URL

### If you are not able to run any of the tools above, please use:

- `https://edc-2022.ngrok.io/voice/answer` - for Answer URL
- `https://edc-2022.ngrok.io/voice/event` - for Event URL

![App Capabilities >> Voice](/voice/app_capabilities.png)

Don't forget to press **Save changes**.
