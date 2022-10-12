---
title: "Vonage App Setup"
weight: 1
---

Your Vonage application has currently the Messages capability only - we'll add Voice to the mix.

## App Capabilities >> Voice

Navigate to your application and click the **Edit** button.

![App summary](/voice/app.png?classes=thumbnail_lg)

Under **Capabilities**, toggle the switch besides **Voice**. This will enable the use of the Voice APIs with your app and setting 3 URL to be used as webhooks.

If you using ngrok, enter your given URL followed by the respective paths, changing the HTTP method to **HTTP POST**:

- **POST: https://subdomain.ngrok.io/voice/answer** - for Answer URL
- **POST: https://subdomain.ngrok.io/voice/event** - for Event URL

#### **Please double-check that you selected POST as the HTTP method**

![App Capabilities >> Voice](/voice/app_capabilities.png?classes=thumbnail_lg)

Don't forget to press **Save changes**.
