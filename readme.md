# TextBox Types and Input Modes

Input fields can be created using a variety of types, including `time`, `datetime`, `week`, `month` or `colour`. When displayed in the browser, some of these types come with built-in controls that make the data collection easy for users. This module allows you to convert the standard Stadium TextBox control into any of these types. [Read More On TextBox Types](https://www.w3schools.com/html/html_form_input_types.asp)

Input fields can also be defined to have two different input modes, namely `numeric` or `email`. When set to one of these, mobile devices adjust the keyboard shown ot the user accordingly. [Read More On Input Modes](https://www.w3schools.com/TAgs/att_inputmode.asp)

 https://github.com/stadium-software/textbox-types/assets/2085324/7854e18e-df60-4e1b-99a5-7fd1b8032395

# Version 
1.1 Initial

## Changes
1.1 Added support for input modes

## Application Setup
1. Check the *Enable Style Sheet* checkbox in the application properties

## Global Script Setup
1. Create a Global Script called "TextBoxType"
3. Drag a *JavaScript* action into the script
4. Add the Javascript below unchanged into the JavaScript code property
```javascript
/* Stadium Script Version 1.1 https://github.com/stadium-software/textbox-types */
const INPUT_TYPE_PREFIX = "stadium-input-type-";
const INPUT_MODE_PREFIX = "stadium-input-mode-";
const fields = document.querySelectorAll(`[class*="${INPUT_TYPE_PREFIX}"], [class*="${INPUT_MODE_PREFIX}"]`);
fields.forEach((field) => {
    const input = field.querySelector("input");
    if (!input) return; // Guard clause
    const classes = field.className.split(" ");
    const typeClass = classes.find((cls) => cls.startsWith(INPUT_TYPE_PREFIX));
    if (typeClass) {
        input.type = typeClass.replace(INPUT_TYPE_PREFIX, "");
    }
    const modeClass = classes.find((cls) => cls.startsWith(INPUT_MODE_PREFIX));
    if (modeClass) {
        input.inputMode = modeClass.replace(INPUT_MODE_PREFIX, "");
    }
});
```

## Page Setup
1. Drag *TextBox* control to a page

### TextBox Types
2. Add a class that begins with "stadium-input-type-" and ends with the desired [type](https://www.w3schools.com/html/html_form_input_types.asp) to the control classes property, for example
   1. stadium-input-type-**time**
   2. stadium-input-type-**datetime-local**
   3. stadium-input-type-**week**
   4. stadium-input-type-**month**
   5. stadium-input-type-**color**

### Input Modes
3. Add a class that begins with "stadium-input-mode-" and ends with the desired [mode](https://www.w3schools.com/TAgs/att_inputmode.asp) to the control classes property, for example
   1. stadium-input-type-**numeric**
   2. stadium-input-type-**email**

## Page.Load Setup
1. Drag the Global Script called "TextBoxType" into the Page.Load event handler

