## Get User Input Data

In this module, you will retrieve the user inputs when the user click the button.

**:bulb: New concepts**
- [Text Input](https://www.wix.com/velo/reference/$w/textinput) Editor Element
- [Button](https://www.wix.com/velo/reference/$w/button/onclick) onClick Events

**:white_check_mark: Step-by-Step Instructions**

1. In order to get the values from the users when they type into your input fields, you'll need to retrieve the value from the field.  

2. Select the _button_ element and in the **Properties and Events** panel, find the onClick function. Add an onClick to your button. The skeleton code should look like this:
```JavaScript
export function signUpButton_click(event) {
	// This function was added from the Properties & Events panel. To learn more, visit http://wix.to/UcBnC-4
	// Add your code for this event here:
}
```

3. In this event, you'll want to get the values in the 2 input fields. Define a variable and retrieve the value from each field. Use the $w notation to access the fields.
```JavaScript
let name = $w('#nameInput').value;
let phoneNum = $w('#phoneNumberInput').value;
```  


:fast_forward: Next Module => [Save data into the database](SAVE_DATA.md)
