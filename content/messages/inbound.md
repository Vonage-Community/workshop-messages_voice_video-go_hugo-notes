---
title: "Inbound SMS"
weight: 3
---

Your app will also display a console message when an inbound message is received on the number associated with the app. Reply to the message you just received to see it in action:

```yml
-----------------------
URL: http://subdomain.loca.lt/messages/inbound
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
-----------------------
```

## Messages API Logs

A log of received messages can be found in the Dashboard, under Logs > [Messages Logs](https://dashboard.nexmo.com/messages/logs) - select **Direction** as **Inbound** and perform a seearch

![Messages Logs](/messages/messages_logs_inbound.png)