---
title: "Send an SMS"
weight: 2
---

## 1. SMS Composer

Inside the **public** folder create a new file named **message.html**, with the following content:

```html
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
  <div class="flex items-center justify-center py-8 text-gray-700">
    <form class="space-y-6" action="/messages/send" method="POST">
      <h1 class="text-2xl text-gray-900">Send an SMS</h1>
      <div>
        <label for="recipient">Recipient</label>
        <input id="recipient" name="recipient" type="phone" autocomplete="phone" required class="mt-1 w-full rounded-md border border-gray-300 px-3 py-2 text-gray-900 placeholder-gray-500" placeholder="">
      </div>
      <div>
        <label for="message">Message</label>
        <textarea id="message" name="message" rows="5" class="mt-1 w-full rounded-md border border-gray-300 px-3 py-2 text-gray-900 placeholder-gray-500" placeholder=""></textarea>
      </div>
      <button type="submit" class="w-full rounded-md border bg-indigo-600 hover:bg-indigo-700 py-2 px-4 text-white">
        Send
      </button>
    </form>
  </div>
</body>
</html>
```

This will serve as the form to compose the SMS (recipient and content) and will be now available at [http://localhost:3000/message.html](http://localhost:3000/message.html).

## 2. Sending an SMS

Back in **app.js** add the following under "**// Messages - send SMS**":

```js
app.post('/messages/send', function(req, res) {
  const SMS = require("@vonage/server-sdk/lib/Messages/SMS");
  vonage.messages.send(
    new SMS(req.body.message, req.body.recipient, "Vonage"),
    (err, data) => {
      if (err) {
        res.send(err).status(500);
      } else {
        res.send(`Message sent successfully: ${JSON.stringify(data)}`).status(200);
      }
    }
  );
});
```

Now, navigate to [http://localhost:3000/message.html](http://localhost:3000/message.html), complete the form and send an SMS to your mobile.

![First Message](/messages/first_message_trim.png)

## 3. Status events

```yml
-----------------------
URL: http://subdomain.loca.lt/messages/status
{
  to: 'xxx',
  from: 'xxx',
  channel: 'sms',
  message_uuid: 'c6a0e0b9-a1ea-49bb-b618-4f15d6612f6e',
  timestamp: '2022-10-04T22:04:01Z',
  usage: { price: '0.0412', currency: 'EUR' },
  status: 'submitted'
}
-----------------------
-----------------------
URL: http://subdomain.loca.lt/messages/status
{
  to: 'xxx',
  from: 'xxx',
  channel: 'sms',
  message_uuid: 'c6a0e0b9-a1ea-49bb-b618-4f15d6612f6e',
  timestamp: '2022-10-04T22:04:02Z',
  status: 'delivered'
}
-----------------------
```

## 4. Messages API Logs

A log of your sent messages can be found in the Dashboard, under Logs > [Messages Logs](https://dashboard.nexmo.com/messages/logs).

![Messages Logs](/messages/messages_logs_sent.png)