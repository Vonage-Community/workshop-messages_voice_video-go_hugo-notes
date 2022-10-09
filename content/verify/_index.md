---
title: "Verify (2FA)"
weight : 2
---

The Verify API enables you to confirm that you can contact a user at a specific number, so that you can:

- Reach your users at any time, by ensuring that you have their correct phone number
- Protect against fraud and spam, by preventing one user from creating multiple accounts
- Add an extra layer of security to help confirm a user's identity when they want to perform certain activities

## Interface

The Verify section consists of one screen with 3 separate scenarios:

1. to start a verification, the user phone number is required
2. once the verification started, the number as well as the request_id is displayed on the screen, together with a box for the verification code input.
3. once code is submitted and the verification completes, a "logged in" message is displayed

![Verify flow](/verify/interface.jpg)

## Code Structure

All code required for this section is contained in the **_verify** folder of the app:

- **_verify/index.js** - contains the logic for the verification request
- **_verify/start.mustache** - HTML code for screen 1
- **_verify/check.mustache** - HTML code for screen 2
- **_verify/index.mustache** - HTML code for screen 3

![Verify code](/verify/code.png)

## Endpoints

The 4 endpoints in use are:

| HTTP Method | Path               | Purpose |
| ----------- | ------------------ | ----------- |
| GET         | **/**              | verification screen |
| POST        | **/verify/start**  | verification start |
| POST        | **/verify/check**  | verification check |
| GET         | **/verify/logout** | resets the verification so the process can start again |

## API responses

As you complete the verification process, the terminal will display the responses for the verification request:

```yml
{ request_id: 'a2f345392fac41fbb73b83d731b3d3c1', status: '0' }
```

... as well as for the code check:

```yml
{
  request_id: 'a2f345392fac41fbb73b83d731b3d3c1',
  status: '0',
  event_id: '2700000008EF4D2B',
  price: '0.05000000',
  currency: 'EUR',
  estimated_price_messages_sent: '0.04120000'
}
```

Notice that the second one will also include the verification price (€0.5) as well as additional messaging and/or voice rates for attempted and successful verifications.

## Resources

- Documentation : https://developer.vonage.com/verify
- API Reference:  https://developer.vonage.com/api/verify
- Pricing: https://www.vonage.co.uk/communications-apis/verify/pricing/
- Verify v2 (early accesss): https://developer.vonage.com/verify/verify-v2/overview
