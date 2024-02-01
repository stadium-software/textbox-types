# TextBox Types

Input fields can be created using a variety of types, including time, datetime, week, month or colour. When displayed in the browser, some of these types come with built-in controls that make the data collection easy for users. This module allows you to convert the standard Stadium TextBox control into any of these types. [Read more](https://www.w3schools.com/html/html_form_input_types.asp)

# Version 
1.0 Initial

## Application Setup
1. Check the *Enable Style Sheet* checkbox in the application properties

## Global Script Setup
1. Create a Global Script called "TextBoxType"
3. Drag a *JavaScript* action into the script
4. Add the Javascript below into the JavaScript code property
```javascript
/* Stadium Script Version 1.0 */
let classname = "stadium-input-type-";
let fields = document.querySelectorAll('[class*="' + classname + '"]');
for (let i = 0; i < fields.length; i++) {
    let arr = fields[i].getAttribute("class").split(" ");
    let type = findIt(classname, arr);
    fields[i].querySelector("input").setAttribute("type", type.replace(classname, ""));
}
function findIt(needle, haystack) {
	return haystack.find((el) => el.startsWith(needle));
}
```

## Page Setup
1. Drag *TextBox* control to a page
2. Add a class that begins with "stadium-input-type-" and ends with the desired [type](https://www.w3schools.com/html/html_form_input_types.asp) to the control classes property, for example
   1. stadium-input-type-**time**
   2. stadium-input-type-**datetime-local**
   3. stadium-input-type-**week**
   4. stadium-input-type-**month**
   5. stadium-input-type-**color**

## Page.Load Setup
1. Drag the Global Script called "TextBoxType" into the Page.Load event handler

# Styling
This module does not come with any default styling. Below are examples of how TextBoxes using this module can be styled

## Applying the CSS

To apply styling to the TextBoxes, change the CSS below as required and paste it into the StyleSheet element in your Stadium application
```css
/*Colour Controls*/
input[type="color"] {
    width: 40px;
}
/*Time Controls*/
input[type="time"] {
    width: 92px;
}
/*DateTime Controls*/
input[type="datetime-local"] {
    width: 170px;
}
/*Parent Controls*/
.text-box-container:has(input[type="hidden"]) {
    padding: 0;
    margin: 0;
}
```