## Create the Twilio Backend

In this module, you will create backend code to help send a text message.

**:bulb: New concepts**
- Backend Code
- [Wix Secret Manager](https://www.wix.com/velo/reference/wix-secrets-backend)

**:white_check_mark: Step-by-Step Instructions**

1. To access the your backend, you will need to go to your **Backend & Public** code files which is the **{}** icon in your left menu bar.  

2. Create a new JavaScript Web Module under the Backend code files called _twilio.jsw_. You can remove all the sample code from this file.

3. First you will need to import the Twilio helper using import notation.
```JavaScript
import twilio from 'twilio';
```

> NOTE: If you ever need help working with an npm helper in Velo, check back in the Code Packages section and click on the module to see if there is a help file already written! It will include starter code to help you use the package.

4. Create a new function called `sendTextMessage` that takes in a toPhoneNumber. Make sure this function has the export keyword in front of it so you can use it elsewhere in your application.
```JavaScript
export function sendTextMessage(toPhoneNumber){

}
```

5. You need to get you secret information from Twilio to authenticate yourself. Get your Auth Token and SID. It's also a good idea to get your Phone Number from your account. These values will be constant, so you can either hard code it into your backend since this is for demo/challenge purposes or store in the Wix Secret Manager and access it via the [WixSecrets API](https://www.wix.com/velo/reference/wix-secrets-backend). To access it from the secret manager, make sure to import the WixSecrets API and create an asynchronous function to retrieve it.
```JavaScript
import wixSecretsBackend from 'wix-secrets-backend';

function getSecretPhoneNum(){
    return wixSecretsBackend.getSecret("twilioPhoneNumber")
        .then((result) => {
            return result;
        });
}
```

6. In _sendTextMessage_, you will need to create a new authenticated Twilio client before you can call anything. To authenticate the Twilio helper, create a new instance of twilio and pass in your SID and Auth Token.
```JavaScript
const twilioClient = new twilio(twilioAccountSid, twilioAuthToken)
```


7. You can now start working with the the Message resource of the Twilio helper. You want to create a new text message, so you will use the create method from the message resource. Create takes in a JSON object with 3 keys, to, from, and body.
```JavaScript
twilio.messages.create({
        "to": "",
        "from": "",
        "body": ""
        }
    )
```

7. The "to" phone number will be your user's input which is why we need it as a parameter for this function. The "from" phone number will be the number you got from Twilio and either hard coded as a constant or retrieved from the Secret Manager. The "body" will be our trivia question, so add some placeholder text for now. Go ahead and connect these inputs that you have.
```JavaScript
export async function sendTextMessage(toPhoneNumber){
    const twilioAuthToken = await wixSecretsBackend.getSecret('twilioAuthToken');
    const twilioAccountSid = await wixSecretsBackend.getSecret('twilioAccountSid');
    const twilioPhoneNumber = await wixSecretsBackend.getSecret('twilioPhoneNumber');

    const twilioClient = new twilio(twilioAccountSid, twilioAuthToken)

    twilioClient.messages.create({
        "to": toPhoneNumber,
        "from": twilioPhoneNumber,
        "body": "Hello World!"
        }
    )
}
```

8. Using the functional testing tool (the Play icon next to the code line numbers), you can test this out. Click the play icon, add your phone number as the to input to test, and **Run**. You'll receive a message on your phone!

:fast_forward: Next Module => [Get some trivia](TRIVIA_FETCH.md)
