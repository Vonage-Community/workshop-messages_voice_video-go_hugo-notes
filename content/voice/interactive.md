---
title: "Interactivity"
weight : 3
---

## Call Flow

When a call is placed to any of the numbers associated with your app, Vonage will make a HTTP call to your **Answer URL**:

![Call NCCO](/voice/interactive.gif?classes=thumbnail_lg)

### Flow diagram

![Call NCCO](/voice/interactive_flow.png?classes=thumbnail_lg)

## voice/answer

The **voice/answer** endpoint is implemented in **_voice/index.js**:

```js
app.post('/voice/answer', (request, response) => {
  console.log(request.body);
  const from = request.body.from
  response.json([
    { 
      "action": "talk", 
      "text": `<speak>Thank you for calling from <say-as interpret-as='telephone'>${from}</say-as> <break time='1s' /> Press 1 for the current time <break strength='weak' /> 2 to play an audio file <break strength='weak' /> or 3 to find out how to pronounce <break strength='weak' />tomato.</speak>`,
      "bargeIn": true
    },
    {
      action: 'input',
      type: [ 'dtmf' ],
      dtmf: { maxDigits: 1 },
      eventUrl: [`https://${request.get('host')}/voice/dtmf`]
    }
  ]);
});
```

It returns an NCCO with 2 actions:

- a **talk** action with custom tags to affect text interpretation and breaks
- a **input** action that will wait for the user to press one digit which will be pass to another url

## voice/dtmf

The **voice/dtmf** endpoint is implemented in **_voice/index.js**:

```js
app.post('/voice/dtmf', (request, response) => {
  let ncco = []
  switch (request.body.dtmf.digits) {
    case '1':
      ncco.push({
        action: 'talk',
        text: `It is ${(new Date()).toUTCString()}`,
      });
      break;
    case '2':
      ncco.push({
        action: 'stream',
        streamUrl: [ 'https://nexmo-community.github.io/ncco-examples/assets/voice_api_audio_streaming_vonage.mp3'],
      });
      break;
    case '3':
      ncco.push({
        action: 'talk',
        text: "<speak><phoneme alphabet='ipa' ph='təˈmætoː'>Tomato</phoneme> or <phoneme alphabet='ipa' ph='təˈmeɪtoʊ'>tomato</phoneme>. Two nations separated by a common language.</speak>"
      });
      break;
    default:
      ncco.push({
        action: 'talk',
        text: 'Sorry, I did not understand that.',
      });
  }
  ncco = ncco.concat([
    {
      action: 'talk',
      text: "Pick another option or hang up.",
      "bargeIn": true
    },
    {
      action: 'input',
      type: [ 'dtmf' ],
      dtmf: { maxDigits: 1 },
      eventUrl: [`https://${request.get('host')}/voice/dtmf`]
    }
  ]);
  response.json(ncco);
});
```

It returns an NCCO with 3 actions, the first one dependent on the digit pressed before. The third action, repeat the process.

There are lots of different ways you can [control how the Vonage Voice API plays machine-generated text](https://developer.vonage.com/voice/voice-api/guides/customizing-tts).

## Resources

- Documentation : https://developer.vonage.com/voice
- API Reference:  https://developer.vonage.com/api/voice
- NCCO reference: https://developer.vonage.com/voice/voice-api/ncco-reference
- Text to Speech: https://developer.vonage.com/voice/voice-api/guides/text-to-speech
- Customizing Spoken Text: https://developer.vonage.com/voice/voice-api/guides/customizing-tts
- Phonemes: https://developer.vonage.com/voice/voice-api/guides/customizing-tts#phonemes

## Exercise

On the **Answer URL**, customise the NCCO so the text to speech plays with an Australian accent.
