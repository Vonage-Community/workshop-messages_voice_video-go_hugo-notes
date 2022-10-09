---
title: "Voice API"
weight : 4
---

The Vonage Voice API is the easiest way to build high-quality voice applications in the Cloud. With the Voice API you can:

- Build apps that scale with the web technologies you are already using
- Control the flow of inbound and outbound calls in JSON with Nexmo Call Control Objects (NCCO). (Nexmo is now Vonage).
- Record and store inbound or outbound calls
- Create conference calls
- Send text-to-speech messages in 40 languages with different genders and accents

## Interface

The Voice section consists of one screen that shows a form to start a voice call, as well as instructions on how to call and interaction with your application using DTMF (Dual Tone Multi Frequency).

![Make Call](/voice/interface.png?classes=thumbnail_lg)

## Code Structure

All code required for this section is contained in the **_voice** folder of the app:

- **_voice/index.js** - contains the code to display the form, placing the call and handle event and inbound webhooks
- **_voice/index.mustache** - the voice page
- **_voice/talk.mustache** - the place a call form
- **_voice/index.mustache** - the "call & interact with your application" message

![Messages code](/voice/code.png?classes=thumbnail_lg)

## Endpoints

The 5 endpoints in use are:

| HTTP Method | Path              | Purpose                        |
| ----------- | ----------------- | ------------------------------ |
| GET         | **/voice**        | place call form                |
| POST        | **/voice/talk**   | place a call                   |
| POST        | **/voice/event**  | event webhook                  |
| POST        | **/voice/answer** | answer webhook                 |
| POST        | **/voice/answer** | interactive response endpoint  |

## Resources

- Documentation : https://developer.vonage.com/voice
- API Reference:  https://developer.vonage.com/api/voice
- Pricing: https://www.vonage.co.uk/communications-apis/voice/pricing/
