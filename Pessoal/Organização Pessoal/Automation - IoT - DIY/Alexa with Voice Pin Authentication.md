---

---
[https://stackoverflow.com/questions/64104762/alexa-skill-how-to-make-a-voice-pin-authentication](https://stackoverflow.com/questions/64104762/alexa-skill-how-to-make-a-voice-pin-authentication)

![[apple-touch-icon2.png]]

I'm new to Alexa skill development. I'm trying to create a voice pin authentication.

This is what I'm trying to achieve:

*User: "Turn ON the light"*

*Alexa: "What is your security pin?"*

*User: "6456" (Wrong pin)*

*Alexa: "Authentication failed! Please try again."*

*User: "1234" (Correct pin)*

*Alexa: "Turning ON the light!"*

If the user tells the correct pin the first time there is no issue, but if the user tells a wrong pin the first time Alexa just says the reprompt message and doesn't take the new pin value, how will I get the new pin value and check that pin once again in the same intent handler?

This is my code:

```plain text
const RemoteControlIntentHandler = {
canHandle(handlerInput) {
    return Alexa.getRequestType(handlerInput.requestEnvelope) === 'IntentRequest'
        && Alexa.getIntentName(handlerInput.requestEnvelope) === 'RemoteControlIntent';
},
handle(handlerInput) {
    var speakOutput = '';
    var userPin = handlerInput.requestEnvelope.request.intent.slots.securityPin.value;

    if (userPin !== userSecurityPin) {
        speakOutput = 'Authentication Failed! Please retry!';

        return handlerInput.responseBuilder
            .speak(speakOutput)
            .reprompt(speakOutput)
            .getResponse();

    } else {
        speakOutput = 'Turning ON the light!';

        return handlerInput.responseBuilder
            .speak(speakOutput)
            .reprompt('add a reprompt if you want to keep the session open for the user to respond')
            .getResponse();

    }
}

```