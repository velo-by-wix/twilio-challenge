## Install the Twilio NPM Helper

In this module, you will access the NPM package manager in Velo to install Twilio.

**:bulb: New concepts**
- NPM Package Manager

**:white_check_mark: Step-by-Step Instructions**

1. To access the package manager, you will need to go to your **Code Packages** which is the box icon in your left menu bar.  

2. Under **npm**,

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

:fast_forward: Next Module => [Install Twilio](INSTALL_TWILIO.md)
