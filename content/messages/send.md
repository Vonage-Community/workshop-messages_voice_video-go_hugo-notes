---
title: "Send an SMS"
weight: 2
---

To send an SMS, simply enter your phone number and, optionally, change the default message:

![Send Message](/messages/interface.png?classes=thumbnail_lg)

## vonage.messages.send

The code to send an SMS is located in **_messages/index.js** under the **/messages/send** endpoint:

```js
const SMS = require("@vonage/server-sdk/lib/Messages/SMS");
const sms = new SMS(
  request.body.message, 
  request.body.recipient, 
  process.env.VONAGE_NUMBER
);

vonage.messages.send(sms, (error, data) => {
  ...
});
```

The console will show the send result:

```yml
{ message_uuid: 'c9cc9dfb-2f12-426c-8422-f73d96198745' }
```

As the sending operation will happen asyncronously, only a **message_uuid** is returned.

## Status events

As the message progresses through its lifecycle, events sent to the configured **Status URL**.

### Message submitted

```yml
{
  to: 'xxx',
  from: 'xxx',
  channel: 'sms',
  message_uuid: 'c6a0e0b9-a1ea-49bb-b618-4f15d6612f6e',
  timestamp: '2022-10-04T22:04:01Z',
  usage: { price: '0.0412', currency: 'EUR' },
  status: 'submitted'
}
```

### Message delivered

```yml
{
  to: 'xxx',
  from: 'xxx',
  channel: 'sms',
  message_uuid: 'c6a0e0b9-a1ea-49bb-b618-4f15d6612f6e',
  timestamp: '2022-10-04T22:04:02Z',
  status: 'delivered'
}
```

## Message Logs

A log of your sent messages can be found in the Dashboard, under Logs > [Messages Logs](https://dashboard.nexmo.com/messages/logs).

![Messages Logs](/messages/messages_logs_sent.png)