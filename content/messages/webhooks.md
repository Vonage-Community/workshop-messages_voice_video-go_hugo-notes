---
title: "Webhooks"
weight: 1
---


## 1. Status Webhook

Here what happens when you send a message via the Messages API:

![Sending an SMS](/messages/status_url.gif)

Inside **index.js**, under "**// Messages - status webhook**", add the following:

```js
app.post('/messages/status', (req, res) => {
  showRequest(req, res);
});
```

Any incoming payload to the **/messages/status** endpoint will now be displayed to the console.

## 2. Inbound Webhook

Here what happens when you receive a message via the Messages API:

![Receiving an SMS](/messages/inbound_url.gif)

Under "**// Messages - inbound webhook**", add:

```js
app.post('/messages/inbound', (req, res) => {
  showRequest(req, res);
});
```
