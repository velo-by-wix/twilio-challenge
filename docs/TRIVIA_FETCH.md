## Fetch Trivia Data

In this module, you will create a REST call to fetch data from a Trivia API.

**:bulb: New concepts**
- [Wix Fetch](https://www.wix.com/velo/reference/wix-fetch)

**:white_check_mark: Step-by-Step Instructions**

1. You can use any API, but for this challenge, using the [Open Trivia Database](https://opentdb.com/api_config.php) is the simplest option as it does not require authentication.  

2. First you will need to import the Wix Fetch API. At the top of the _twilio.jsw_ file, import the fetch method from this API.
```JavaScript
import { fetch } from 'wix-fetch';

```

3. Create a new function called _getTrivia()_. It takes in no parameters.
```JavaScript
export function getTrivia(){

}
```

4. This function will fetch a random piece of trivia to share. Wix Fetch works like any other fetch API, so you will define the URL for the API endpoint to fetch and a JSON object with the method as a key value pair for GET. You can get the API endpoint example from Open Trivia Database.
```JavaScript
fetch("https://opentdb.com/api.php?amount=1", {"method":"GET"})
```

5. Since fetch is asynchronous, you will need to wait for the promise to resolve before you can use the data. Once it resolves, the first thing it returns is the status of the call. If it was successful, you can move on to get the data. Check the status of the HTTP Request. If the status is OK, you'll return the JSON of the response which has the data from the call.
```JavaScript
.then((httpResponse) => {
    if (httpResponse.ok) {
       return httpResponse.json();
    };
})
```

6. Now that you've return the data, you can parse out the part you want. Since you only requested 1 trivia question and you know it returned OK, you can look at the results at index 0 to get the question you want.
```JavaScript
.then((json) => {
      return json.results[0].question;
})
```


7. The last thing to double check is that you returned this fetch call from your function. That way you can call it and use the result when it returns.
```JavaScript
return fetch("https://opentdb.com/api.php?amount=1", { "method": "GET" })
    .then((httpResponse) => {
        if (httpResponse.ok) {
           return httpResponse.json();
        };
    }).then((json) => {
        return json.results[0].question;
    });
```

8. You can test this function just like you did for the Twilio text message test. Click on the Play icon next to the function and then click Run. This function doesn't take any inputs, so it is easy to test! Make sure you are seeing a trivia question in the Function Output.

:fast_forward: Next Module => [Let's put it all together!](PUT_TOGETHER.md)
