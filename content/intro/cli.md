---
title: "Vonage CLI"
weight : 2
---

The Vonage CLI allows you to interact with your Vonage account and use our products from the command line.

## 1. Installation

It can be installed via **npm**:

```sh
npm install --location=global @vonage/cli
```

or, if using yarn:

```sh
yarn global add @vonage/cli
```

The **vonage** command is now available to use:

```sh
 vonage --help
```

#### Resources

- Homepage: [developer.vonage.com/application/vonage-cli](https://developer.vonage.com/application/vonage-cli)
- CLI project: [github.com/Vonage/vonage-cli](https://github.com/Vonage/vonage-cli)


## 2. Configuration

Before using the CLI, it needs to be configured with your credentials:

```sh
vonage config:set --apiKey=$VONAGE_API_KEY --apiSecret=$VONAGE_API_SECRET
```

The stored credentials are accessible via:

```sh
vonage config
```

> NB: Credentials are stored in **~/.config/@vonage/cli/vonage.config.json**.

## 3. Check balance

To check your account balance:

```sh
vonage balance
```

## 4. Send an SMS

The CLI has a plugin architecture so tasks for various APIs can be installed. To be able to send an SMS via the CLI, you'll need to install the sms plugin:

```sh
vonage plugins:install @vonage/cli-plugin-sms
```

We now have the **vonage sms** command - you can see how to use it:

```sh
vonage sms --help
```

To send an SMS, copy the snippet below and replace **YOUR_NUMBER** with your mobile number:

```sh
vonage sms --message='A text message sent using the Vonage CLI' --from=Vonage --to=YOUR_NUMBER
```

## 5. Search for a number to rent

In a later section you will be calling your mobile number from a Vonage number that you will need to own. To search for a number to buy:

```sh
vonage numbers:search COUNTRY_CODE --features=SMS,VOICE
```

Please replace **COUNTRY_CODE** with a two digit country code in ISO 3166-1 alpha-2 format. Eg: GB for the United Kingdom, SE for Sweden and US for United States.

```sh
vonage numbers:search US --features=SMS,VOICE
```

A successful response will include the a subset of available numbers, together with their type (eg. landline, mobile), features available (eg, Voice, SMS) amd the monthly recurring cost:

```json
 Country Number      Type       Cost Features  
 ─────── ─────────── ────────── ──── ───────── 
 US      12013753230 mobile-lvn 0.90 VOICE,SMS 
 US      12013753243 mobile-lvn 0.90 VOICE,SMS 
 US      12013770177 mobile-lvn 0.90 VOICE,SMS 
 US      12013771865 mobile-lvn 0.90 VOICE,SMS 
 US      12013815388 mobile-lvn 0.90 VOICE,SMS 
 US      12013815815 mobile-lvn 0.90 VOICE,SMS 
 US      12014196249 mobile-lvn 0.90 VOICE,SMS 
 US      12014293688 mobile-lvn 0.90 VOICE,SMS 
 US      12014725860 mobile-lvn 0.90 VOICE,SMS 
 US      12014739055 mobile-lvn 0.90 VOICE,SMS 
```

#### Resources:

- Documentation page: [developer.vonage.com/numbers/code-snippets/search-available](https://developer.vonage.com/numbers/code-snippets/bsearch-availableuy)
- API Reference: [developer.vonage.com/api/numbers](https://developer.vonage.com/api/numbers)
- [ISO 3166-1 alpha-2 codes](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Current_codes)

## 6. Renting a number

Now that you found a number, you can "buy" it:

```sh
vonage numbers:buy VONAGE_NUMBER COUNTRY_CODE
```

Replacing **VONAGE_NUMBER** and **COUNTRY_CODE** as required:

```sh
vonage numbers:buy 12013753230 US
```

The rented number will appear in your [Dashboard](https://dashboard.vonage.com), under the [Your Numbers section](https://dashboard.nexmo.com/your-numbers).

### 6.1 Local Restrictions

Some country have local regulations for certain numbers -e.g. renting a landline in Sweden requires physical presence in the same local region as the number.

![Number rental requirements](/intro/app_numbers_reqs.png?classes=thumbnail_lg)

### 6.2 "10 DLC"

Major US carriers have announced their requirements for a new standard for application-to-person (A2P) messaging in the USA, which applies to all messaging over 10 digit geographic phone numbers.

Customers using the Vonage SMS and Messages APIs to send traffic from a +1 Country Code 10 Digit Long Code (10 DLC) into US networks will need to register a brand and campaign via the campaign registry (TCR), in order to get approval for sending messages.

#### Resources:

- Documentation page: [developer.vonage.com/numbers/code-snippets/buy](https://developer.vonage.com/numbers/code-snippets/buy)
- API Reference: [developer.vonage.com/api/numbers](https://developer.vonage.com/api/numbers)
- 10 DLC: https://developer.vonage.com/messages/10-dlc/overview
