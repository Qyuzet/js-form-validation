# JavaScript Form Validation

![Form Validation](https://img.shields.io/badge/Form%20Validation-JavaScript-blue)

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## Overview

This repository contains a simple and effective form validation script written in JavaScript. The aim is to provide a lightweight and flexible solution for validating user inputs in web forms, ensuring data integrity and improving user experience.
[TRY NOW!](https://qyuzet.github.io/js-form-validation/)

![image](https://github.com/Qyuzet/js-form-validation/assets/93258081/00c311e2-0069-47ba-bc3e-bbd460c94db6)


## Features

- **Real-time Validation:** Provides instant feedback as users fill out the form fields.
- **Comprehensive Checks:** Validates name, phone number, email, and message fields.
- **User-Friendly Error Messages:** Displays clear and concise error messages for invalid inputs.
- **Stylish Interface:** Modern design with Font Awesome icons for validation feedback.

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/Qyuzet/js-form-validation.git
    ```
2. Navigate to the project directory:
    ```bash
    cd js-form-validation
    ```

## Usage

1. Open the `index.html` file in your web browser to view and test the form validation.

### HTML Structure

The form structure includes the following fields:

- Full Name
- Phone Number
- Email Address
- Message

Each input field has an associated error message span for displaying validation feedback.

```html
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Form Validation</title>
    <link rel="stylesheet" href="style.css" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css" integrity="sha512-SnH5WK+bZxgPHs44uWIX+LLJAJ9/2PkPKZ5QiAj6Ta86w+fsb2TkcmfRyVX3pBnMFcV7oQPJkl9QevSCWr3W6A==" crossorigin="anonymous" referrerpolicy="no-referrer" />
</head>
<body>
    <div class="container">
        <form>
            <i class="fas fa-paper-plane"></i>
            <div class="input-group">
                <label>Full Name</label>
                <input type="text" placeholder="Enter your name" id="contact-name" onkeyup="validateName()" />
                <span id="name-error"></span>
            </div>
            <div class="input-group">
                <label>Phone No.</label>
                <input type="tel" placeholder="0812 3455 8982" id="contact-phone" onkeyup="validatePhone()" />
                <span id="phone-error"></span>
            </div>
            <div class="input-group">
                <label>Email Id</label>
                <input type="email" placeholder="Enter Email" id="contact-email" onkeyup="validateEmail()" />
                <span id="email-error"></span>
            </div>
            <div class="input-group">
                <label>Your Message</label>
                <textarea rows="5" placeholder="Enter your message" id="contact-message" onkeyup="validateMessage()"></textarea>
                <span id="message-error"></span>
            </div>
            <button onclick="return validateForm()">Submit</button>
            <span id="submit-error"></span>
        </form>
    </div>
    <script src="scripts.js"></script>
</body>
</html>
```

### JavaScript Validation

The validation logic is implemented in `scripts.js`. Each input field has a corresponding validation function:

```javascript
var nameError = document.getElementById("name-error");
var phoneError = document.getElementById("phone-error");
var emailError = document.getElementById("email-error");
var messageError = document.getElementById("message-error");
var submitError = document.getElementById("submit-error");

function validateName() {
    var name = document.getElementById("contact-name").value;
    if (name.length == 0) {
        nameError.innerHTML = "Name is required";
        return false;
    }
    if (!name.match(/^[A-Za-z]*\s{1}[A-Za-z]*$/)) {
        nameError.innerHTML = "write full name";
        return false;
    }
    nameError.innerHTML = '<i class="fa-solid fa-circle-check"></i>';
    return true;
}

function validatePhone() {
    var phone = document.getElementById("contact-phone").value;
    if (phone.length == 0) {
        phoneError.innerHTML = "Phone no is required";
        console.log("null value");
        return false;
    }
    if (phone.length !== 12) {
        phoneError.innerHTML = "Phone no should be 12 digits";
        console.log("should 10");
        return false;
    }
    if (!phone.match(/^[0-9]{12}$/)) {
        phoneError.innerHTML = "Only digits please";
        console.log("char");
        return false;
    }
    phoneError.innerHTML = '<i class="fa-solid fa-circle-check"></i>';
    return true;
}

function validateEmail() {
    var email = document.getElementById("contact-email").value;
    if (email.length == 0) {
        emailError.innerHTML = "Email is required";
        return false;
    }
    if (!email.match(/^[A-Za-z\._\-[0-9]*[@][A-Za-z]*[\.][a-z]{2,4}$/)) {
        emailError.innerHTML = "Email Invalid";
        return false;
    }
    emailError.innerHTML = '<i class="fa-solid fa-circle-check"></i>';
    return true;
}

function validateMessage() {
    var message = document.getElementById("contact-message").value;
    var required = 30;
    var left = required - message.length;
    if (left > 0) {
        messageError.innerHTML = left + " more character required";
        return false;
    }
    messageError.innerHTML = '<i class="fa-solid fa-circle-check"></i>';
    return true;
}

function validateForm() {
    if (!validateName() || !validatePhone() || !validateEmail() || !validateMessage()) {
        submitError.style.display = "block";
        submitError.innerHTML = "Please fix error to submit";
        setTimeout(function () {
            submitError.style.display = "none";
        }, 3000);
        return false;
    }
}
```

### CSS Styling

The styling for the form is provided in `style.css`:

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Poppins", sans-serif;
}

.container {
    width: 100%;
    height: 100vh;
    background: #141a34;
    display: flex;
    align-items: center;
    justify-content: center;
}

.useful-links {
    position: absolute;
    top: 5%;
    right: 5%;
}

.useful-links a {
    display: block;
    color: #fff;
    text-decoration: none;
}

.container form {
    width: 90%;
    max-width: 500px;
    padding: 50px 30px 20px;
    background: #fff;
    border-radius: 4px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.5);
    position: relative;
}

.fa-paper-plane {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%, -50%);
    background: #fff;
    font-size: 26px;
    padding: 20px;
    border-radius: 50%;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}

.input-group {
    width: 100%;
    display: flex;
    align-items: center;
    margin: 10px 0;
    position: relative;
}

.input-group label {
    flex-basis: 28%;
}

.input-group input,
.input-group textarea {
    flex-basis: 68%;
    background: transparent;
    border: 0;
    outline: 0;
    padding: 10px 0;
    border-bottom: 1px solid #999;
    color: #333;
    font-size: 16px;
}

::placeholder {
    font-size: 14px;
}

form button {
    background: #141a34;
    color: #fff;
    border-radius: 4px;
    border: 1px solid rgba(255, 255, 255, 0.7);
    padding: 10px 40px;
    outline: 0;
    cursor: pointer;
    display: block;
    margin: 30px auto 10px;
}

.input-group span {
    position: absolute;
    bottom: 12px;
    right: 17px;
    font-size: 14px;
    color: red;
}

#submit-error {
    columns: red;
}

.input-group span i {
    color: seagreen;
}
```

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements

 or suggestions.

## License

This project is licensed under the MIT License.

## Acknowledgements

- [Font Awesome](https://fontawesome.com/) for the icons used in validation feedback.
- [Poppins](https://fonts.google.com/specimen/Poppins) for the font.
