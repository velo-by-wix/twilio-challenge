## Let's put it all together!

In this module, you will connect your Trivia response to your Twilio text and send your text from your user input.

**:bulb: New concepts**
- Accessing backend code in your frontend

**:white_check_mark: Step-by-Step Instructions**

1. Now that you have your working Trivia REST call, you can use that as your body of your Twilio text message. Call the _getTrivia_ function in your _sendTextMessage_ function. Remember that this is promised so you will need to await it.
```JavaScript
let trivia = await getTrivia();

```


2. Since you now have a trivia question, you can update the body of the text to send the trivia question instead of Hello World.
```JavaScript
twilioClient.messages.create({
        "to": toPhoneNumber,
        "from": twilioPhoneNumber,
        "body": trivia
    });
```

3. Now it's time to connect this to your frontend user input. Back in the _HOME_ page code, import the _sendTextMessage_ function using the import notion. You must traverse the file structure to get to the backend code files in your import statement.
```JavaScript
import { sendTextMessage } from 'backend/twilio.jsw';
```

4. Finall, you can call _sendTextMessage_ in your button onClick event. Pass in the _phoneNum_ variable value to this function to send the user input to the Twilio text message!
```JavaScript
sendTextMessage(phoneNum);
```

5. Go ahead and publish your application and try it out yourself! Can you answer the trivia question?

:boom: **Hurray! You've completed the challenge. You have now acquired the skills to create your own web application using Velo!** :confetti_ball:
