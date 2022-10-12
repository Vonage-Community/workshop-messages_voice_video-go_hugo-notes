---
title: "Simple API calls"
weight : 1
---

In this section, you will start making couple of simple API calls to get familiar with the Vonage APIs.

### API Key and Secret

Your API Key and Secret are available on your [Dashboard](https://dashboard.nexmo.com) under the [API Settings section](https://dashboard.nexmo.com/settings).

We will set them up as environment variables in your terminal to use them in API requests:

```sh
export VONAGE_API_KEY="xxx"
export VONAGE_API_SECRET="xxx"
```

To check they are set correctly:

```sh
echo $VONAGE_API_KEY
```

and

```sh
echo $VONAGE_API_SECRET
```

## 1. Check Your Balance

To check your balance, type to following in your terminal:

```sh
curl "https://rest.nexmo.com/account/get-balance?api_key=$VONAGE_API_KEY&api_secret=$VONAGE_API_SECRET"
```

A successful response will include the remaining credit and the autoreload status:

```json
{"value":81.68078129,"autoReload":false}
```

> **curl** is a utility that allows one to make HTTP calls from a terminal and it comes preinstalled on most operating systems. Download packages are available at: [curl.se/download.html](https://curl.se/download.html).
>
> A similar tool, with a visual interface, is [Postman](https://www.postman.com/).

Your balance will be consumed as APIs calls are being placed, be that an SMS being sent or received or a Voice call being made. You only pay for what you use. Full pricing is available at <https://www.vonage.co.uk/communications-apis/pricing/>.

#### Resources:

- Documentation page: [developer.vonage.com/account/code-snippets/account-balance](https://developer.vonage.com/account/code-snippets/account-balance)
- API Reference: [developer.vonage.com/api/account#getAccountBalance](https://developer.vonage.com/api/account#getAccountBalance)

## 2. Send an SMS

Copy and paste the snippet below into your terminal, replacing **YOUR_NUMBER** with your mobile number:

> NB: All phone number used with the Vonage APIs must be in the [E.164 format](https://en.wikipedia.org/wiki/E.164). Here are couple of examples:
>  - US: 12065550100
>  - UK: 441134960000
>  - SE: 46701740605

```sh
curl -X "POST" "https://rest.nexmo.com/sms/json" \
  -d "api_key=$VONAGE_API_KEY" \
  -d "api_secret=$VONAGE_API_SECRET" \
  -d "text=A first text message sent using the Vonage SMS API" \
  -d "from=Vonage" \
  -d "to=YOUR_NUMBER"
```

A successful response will include the message id as well as its cost and the remaining balance of your account:

```json
{"messages":[{"to":"xxx","message-id":"51a4b791-d4d8-4d4b-b05a-783654d4d7b2","status":"0","remaining-balance":"85.68078129","message-price":"0.04120000","network":"23433"}],"message-count":"1"}
```

#### Resources:

- Documentation page: [developer.vonage.com/messaging/sms/code-snippets/send-an-sms](https://developer.vonage.com/messaging/sms/code-snippets/send-an-sms)
- API Reference: [developer.vonage.com/api/sms#send-an-sms](https://developer.vonage.com/api/sms#send-an-sms)
