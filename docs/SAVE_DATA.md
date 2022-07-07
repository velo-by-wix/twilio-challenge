## Save the data in your Database

In this module, you will save the user inputs in your database.

**:bulb: New concepts**
- [Wix Data API](https://www.wix.com/velo/reference/wix-data)

**:white_check_mark: Step-by-Step Instructions**

1. Now that you have the data from the inputs, you have to store them in the database. First, you need to import the WixData API. The best way to manage import statements is by adding them at the top of your code files. 
```JavaScript
import wixData from 'wix-data';
```

2. Back in your button onClick event, you need to create a JSON object with the inputs and the fields they should be stored in using the key of the JSON as the field key and the value the retrieved inputs.
```JavaScript
let dataToStore = {
  "title": name,
  "phoneNumber": phoneNum
}
```

3. The Wix Data API gives you CRUD (and more) access to your content collections. You can use the insert method to pass in the collection ID you noted earlier and the dataToStore object.  
```JavaScript
wixData.insert("UserList", dataToStore);
```  

4. Inserts happen asynchronously, so if you want to clear the data and/or show a success message after it successfully inserts, you can use promises and `.then()` to do so after it resolves.
```JavaScript
wixData.insert("UserList", dataToStore)
		.then((result) => {
			console.log(result);
			$w('#nameInput, #phoneNumberInput').value = "";
		});
```

5. If you have set everything up correctly, when you preview your website using the **Preview** button on the top right of the screen, enter some test data. Go back to the Editor and to the Database tab via the left side menu bar. Check and verify that the data is stored.

> COMMON ISSUES: Some reasons your data may not be saved is because of the follow
>  A) you have not set the permissions of the database to allow anyone to Insert Data
>  B) you do not have the Field Keys spelled properly (capitalization counts!)
>  C) you do not have the Collection ID spelled properly (capitalization counts!)


:fast_forward: Next Module => [Install Twilio](INSTALL_TWILIO.md)
