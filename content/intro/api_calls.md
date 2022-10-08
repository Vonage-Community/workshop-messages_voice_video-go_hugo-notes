---
title: "Simple API calls"
weight : 1
---

In this section, you will start making couple of simple API calls to get familiar with the Vonage APIs.

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

**Resources**:

- Documentation page: [developer.vonage.com/account/code-snippets/account-balance](https://developer.vonage.com/account/code-snippets/account-balance)
- API Reference: [developer.vonage.com/api/account#getAccountBalance](https://developer.vonage.com/api/account#getAccountBalance)

---

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

**Resources**:

- Documentation page: [developer.vonage.com/messaging/sms/code-snippets/send-an-sms](https://developer.vonage.com/messaging/sms/code-snippets/send-an-sms)
- API Reference: [developer.vonage.com/api/sms#send-an-sms](https://developer.vonage.com/api/sms#send-an-sms)

---

## 3. Search for a number to rent

Vonage enables one to rent numbers to be used to make calls. In a later section you will be calling your mobile number from a Vonage number that you will buy next. In the snippet below, replace **COUNTRY_CODE** with a two digit country code in ISO 3166-1 alpha-2 format. Eg: GB for the United Kingdom, SE for Sweden and US for United States.

```sh
curl "https://rest.nexmo.com/number/search?api_key=$VONAGE_API_KEY&api_secret=$VONAGE_API_SECRET&country=COUNTRY_CODE"
```

For Sweden:

```sh
curl "https://rest.nexmo.com/number/search?api_key=$VONAGE_API_KEY&api_secret=$VONAGE_API_SECRET&country=SE"
```

A successful response will include the total count and a subset of available numbers, together with their type (eg. landline, mobile), features available (eg, Voice, SMS) amd the monthly recurring cost. Here is the current one for Sweden:

```json
{"count":53,"numbers":[
  {"country":"SE","msisdn":"46187511097","cost":"0.90","type":"landline","features":["VOICE"]},  
  {"country":"SE","msisdn":"46313616022","cost":"0.90","type":"landline","features":["VOICE"]},
  ...
  {"country":"SE","msisdn":"46769436255","cost":"4.00","type":"mobile-lvn","features":["VOICE","SMS"]
  ...
]}
```

... and for US:

```sh
curl "https://rest.nexmo.com/number/search?api_key=$VONAGE_API_KEY&api_secret=$VONAGE_API_SECRET&country=US"
```

```json
{"count":1306895,"numbers":[
  {"country":"US","msisdn":"12013815890","cost":"0.90","type":"mobile-lvn","features":["VOICE","SMS"]},
  {"country":"US","msisdn":"12014293560","cost":"0.90","type":"mobile-lvn","features":["VOICE","SMS"]},
  {"country":"US","msisdn":"12014293594","cost":"0.90","type":"mobile-lvn","features":["VOICE","SMS"]},
  ...
]}
```

> 

**Resources**:

- Documentation page: [developer.vonage.com/numbers/code-snippets/search-available](https://developer.vonage.com/numbers/code-snippets/bsearch-availableuy)
- API Reference: [developer.vonage.com/api/numbers](https://developer.vonage.com/api/numbers)
- [ISO 3166-1 alpha-2 codes](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Current_codes)

---

## 4. Renting a number

Now that we found a number, copy the snippet below, replacing **VONAGE_NUMBER** with one of the numbers returned on the last search (the one performed for US):

```sh
curl -X "POST" "https://rest.nexmo.com/number/buy" \
  -d "api_key=$VONAGE_API_KEY" \
  -d "api_secret=$VONAGE_API_SECRET" \
  -d "country=US" \
  -d "msisdn=VONAGE_NUMBER"
```

Please pick an US number from the list returned by the last call.

A success response will look like:

```yml
{"error-code":"200","error-code-label":"success"}
```

If the number is not available (e.g. rented by someone else), the following error response will be sent:

```yml
{"error-code":"420","error-code-label":"method failed"}
```

The rented number will appear in your [Dashboard](https://dashboard.vonage.com), under the [Your Numbers section](https://dashboard.nexmo.com/your-numbers).

**Resources**:

- Documentation page: [developer.vonage.com/numbers/code-snippets/buy](https://developer.vonage.com/numbers/code-snippets/buy)
- API Reference: [developer.vonage.com/api/numbers](https://developer.vonage.com/api/numbers)
