---
title: "Inbound SMS"
weight: 3
---

The workshop is also configured to receive inbound messages.

## Inbound URL

When you receive a message via the Messages API, the inbound URL will receive an request with all the message information:

![Receiving an SMS](/messages/inbound_url.gif?classes=thumbnail_lg)

```yml
{
  to: 'xxx',
  from: 'xxx',
  channel: 'sms',
  message_uuid: '27bf01c4-6eb4-4085-af08-89e6bcdb2042',
  timestamp: '2022-10-04T22:26:08Z',
  usage: { price: '0.0057', currency: 'EUR' },
  message_type: 'text',
  text: 'Hello Back!',
  sms: { num_messages: '1' }
}
```

## Messages API Logs

A log of received messages can be found in the Dashboard, under Logs > [Messages Logs](https://dashboard.nexmo.com/messages/logs) - select **Direction** as **Inbound** and perform a seearch

![Messages Logs](/messages/messages_logs_inbound.png)