---
title: "Place call"
weight : 2
---

To place a call, simply enter your phone number and, optionally, change the default message:

![Place a Call](/voice/interface.png?classes=thumbnail_lg)

## vonage.calls.create

The code to send an SMS is located in **_messages/index.js** under the **/messages/send** endpoint:

```js
vonage.calls.create({
  to: [{ type: 'phone', number: request.body.phone }],
  from: { type: 'phone', number: process.env.VONAGE_NUMBER },
  ncco: [{ "action": "talk", "text": request.body.message }]
}, (err, data) => {
  ...
});
```

The console will show the result of the operation:

```yml
{
  uuid: '14e69552-aa8e-4ce4-a723-931ddc5fd7e7',
  status: 'started',
  direction: 'outbound',
  conversation_uuid: 'CON-b8620fa2-224e-4b51-a89e-b935fd59d29a'
}
```

> NB: a call is placed within the context of a conversation, with the caller and calle part of it.

## NCCO

A Call Control Object (NCCO) is a JSON array of actions that is used to control the flow of a Voice API Call.

In the code above you are constructing an NCCO with a single talk action:

```json
[
  {
    "action": "talk",
    "text": "This is a text to speech call from Vonage"
  }
]
```

You will learn more about NCCO in the next section.

## Call Flow

Here what happens when you place a call via the Voice API with an NCCO:

![Placing a call](/voice/place_a_call.gif?classes=thumbnail_lg)

### Flow diagram

![Placing a call](/voice/place_a_call_flow.png?classes=thumbnail_lg)

## Event URL

The console will show events are they come through:

```yml
-----------------------
2022-10-09T16:51:01.634Z
URL: http://pardel.ngrok.io/voice/event
{
  headers: {},
  from: 'xxx',
  to: 'xxx',
  uuid: '6a42647d-64cc-4dfe-a997-f9b9c578fd0b',
  conversation_uuid: 'CON-15f7ae85-e045-48aa-89e8-57a3cf3f1b91',
  status: 'started',
  direction: 'outbound',
  timestamp: '2022-10-09T16:51:01.496Z'
}
-----------------------
-----------------------
2022-10-09T16:51:01.720Z
URL: http://pardel.ngrok.io/voice/event
{
  headers: {},
  from: 'xxx',
  to: 'xxx',
  uuid: '6a42647d-64cc-4dfe-a997-f9b9c578fd0b',
  conversation_uuid: 'CON-15f7ae85-e045-48aa-89e8-57a3cf3f1b91',
  status: 'ringing',
  direction: 'outbound',
  timestamp: '2022-10-09T16:51:01.496Z'
}
-----------------------
-----------------------
2022-10-09T16:51:03.900Z
URL: http://pardel.ngrok.io/voice/event
{
  start_time: null,
  headers: {},
  rate: null,
  from: 'xxx',
  to: 'xxx',
  uuid: '6a42647d-64cc-4dfe-a997-f9b9c578fd0b',
  conversation_uuid: 'CON-15f7ae85-e045-48aa-89e8-57a3cf3f1b91',
  status: 'answered',
  direction: 'outbound',
  network: null,
  timestamp: '2022-10-09T16:51:03.824Z'
}
-----------------------
-----------------------
2022-10-09T16:51:07.250Z
URL: http://pardel.ngrok.io/voice/event
{
  headers: {},
  end_time: '2022-10-09T16:51:07.000Z',
  uuid: '6a42647d-64cc-4dfe-a997-f9b9c578fd0b',
  network: '23433',
  duration: '4',
  start_time: '2022-10-09T16:51:03.000Z',
  rate: '0.10000000',
  price: '0.00666667',
  from: 'xxx',
  to: 'xxx',
  conversation_uuid: 'CON-15f7ae85-e045-48aa-89e8-57a3cf3f1b91',
  status: 'completed',
  direction: 'outbound',
  timestamp: '2022-10-09T16:51:07.150Z'
}
-----------------------
```

## HTTP GET Webhooks

If **HTTP GET** is selected for the **Event URL**, the data will be sent as GET parameters:

```sh
GET /voice/event?headers=%7B%7D&end_time=2022-10-09T14:50:41.000Z&uuid=d0bb18e9-d80b-4053-904c-016da2111ac7&network=23433&duration=4&start_time=2022-10-09T14:50:37.000Z&rate=0.10000000&price=0.00666667&from=xxx&to=xxx&conversation_uuid=CON-bdaed8df-d9d3-4f39-9ce3-54e51bad36a3&status=completed&direction=outbound&timestamp=2022-10-09T14:50:40.359Z
```

## Resources

- Documentation : https://developer.vonage.com/voice
- API Reference:  https://developer.vonage.com/api/voice
- NCCO: https://developer.vonage.com/voice/voice-api/guides/ncco
