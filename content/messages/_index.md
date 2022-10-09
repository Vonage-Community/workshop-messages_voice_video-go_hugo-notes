---
title: "Messages API"
weight : 3
---

In this section, you are going to learn how to communicate with customers over their preferred channels using Vonage’s Messages and Dispatch APIs.

The Messages API allows you to send and in some cases receive messages over the following communications channels:

- SMS
- MMS
- Facebook Messenger
- Viber
- WhatsApp

![Messages API](/messages/messages-overview.png)

> NB: The SMS' you sent earlier (via CLI and direct API call) were sent via the Vonage SMS API and don't require dedicated setup.

## Supported Features

A full list of supported features is available on the Developer Portal [Messages Overview page](https://developer.vonage.com/messages/overview#supported-features).

## Interface

The Messages section consists of one screen that shows a form to send a message:

![Send Message](/messages/interface.png?classes=thumbnail_lg)

## Code Structure

All code required for this section is contained in the **_messages** folder of the app:

- **_messages/index.js** - contains the code to display the form, sending the message and handle event and inbound webhooks
- **_messages/form.mustache** - the message form

![Messages code](/messages/code.png)

## Endpoints

The 4 endpoints in use are:

| HTTP Method | Path                 | Purpose         |
| ----------- | -------------------- | --------------- |
| GET         | **/messages**        | message form    |
| POST        | **/messages/send**   | send message    |
| POST        | **/messages/status** | status webhook  |
| GET         | **messages/inbound** | inbound webhook |

## Resources

- Documentation : https://developer.vonage.com/messages
- API Reference:  https://developer.vonage.com/api/messages-olympus
- Pricing: https://www.vonage.co.uk/communications-apis/messages/pricing/
