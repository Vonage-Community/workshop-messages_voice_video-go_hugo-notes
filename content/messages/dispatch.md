---
title: "Appendix: Dispatch API"
weight: 90
---

[Dispatch API](https://developer.vonage.com/dispatch/overview) enables developers to send messages to users using a multiple channel strategy. An example workflow might specify a message to be sent a message via Facebook Messenger, and if that message is not read then the user can be sent a message via Viber. If that message is also not read, a user could then be sent a message via SMS.

![Dispatch API](/messages/dispatch-overview.png?classes=thumbnail_lg)

Here is an example:

```json
"template":"failover",
"workflow": [
  {
    "from": { "type": "messenger", "number": "YOUR_FB_ID" },
    "to":   { "type": "messenger", "number": "RECIPIENT_FB_ID" },
    "message": {
      "content": {
        "type": "text",
        "text": "This is a Message sent via the Dispatch API"
      }
    },
    "failover":{
      "expiry_time": 3600,
      "condition_status": "read"
    }
  },
  {
    "from": { "type": "viber_service_msg", "id": "YOUR_VIBER_ID" },
    "to":   { "type": "viber_service_msg", "number": "DESTINATION_NUMBER" },
    "message": {
      "content": {
        "type": "text",
        "text": "This is a Message sent via the Dispatch API"
      }
    },
    "failover":{
      "expiry_time": 7200,
      "condition_status": "delivered"
    }
  },
  {
    "from": { "type": "sms", "number": "VONAGE_NUMBER" },
    "to":   { "type": "sms", "number": "DESTINATION_NUMBER" },
    "message": {
      "content": {
        "type": "text",
        "text": "This is a Message sent via the Dispatch API"
      }
    }
  }
]
```

## Resources

- Documentation : https://developer.vonage.com/dispatch
- API Reference:  https://developer.vonage.com/api/dispatch
- Pricing: https://www.vonage.co.uk/communications-apis/dispatch/pricing/
