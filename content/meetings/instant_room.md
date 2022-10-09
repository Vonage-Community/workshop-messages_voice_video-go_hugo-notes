---
title: "Instant Room"
weight: 2
---

## Create Room

To create a Meetings Instant Room, copy in the Terminal the snippet shown on the page.

![Create Room](/meetings/interface.png?classes=thumbnail_lg)

Running the command will return a JSON response with the details about the room you just created:

```json
{
  "id": "8ea7e37f-e9f7-41b0-93cc-9fee936dc3f2",
  "display_name": "EDC 2022",
  "metadata": null,
  "type": "instant",
  "expires_at": "2022-10-09T21:27:40.093Z",
  "recording_options": {
    "auto_record": false,
    "record_only_owner": false
  },
  "meeting_code": "959897203",
  "_links": {
    "host_url": {
      "href": "https://meetings.vonage.com/?room_token=959897203&participant_token=xxx"
    },
    "guest_url": {
      "href": "https://meetings.vonage.com/959897203"
    }
  },
  "created_at": "2022-10-09T21:17:40.093Z",
  "is_available": true,
  "expire_after_use": false,
  "theme_id": null,
  "initial_join_options": {
    "microphone_state": "default"
  }
}
```

## The Links

The response provides 2 URLs:

- **host_url** - gives the visitor additional controls
- **guest_url** - regular participant access

## Authentication with JWTs

JSON Web Tokens (JWT) are used by the Meetings API to authenticate your requests. Vonage provides an [JWT Generator](https://developer.vonage.com/jwt) to create a JWT using your application ID and private key.

However, it is also possible to create one using the Node Server SDK, as shown in **_meetings/index.js**:

```js
const jwt = vonage.generateJwt();
```

## Resources

- JWT : https://jwt.io/
- API Reference: https://developer.vonage.com/api/meetings
- Create an Instant Room: https://developer.vonage.com/meetings/code-snippets/create-instant-room
