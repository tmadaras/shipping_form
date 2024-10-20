# shipping_form
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shipping Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .form-container {
            max-width: 600px;
            margin: auto;
            padding: 20px;
            background-color: #f9f9f9;
            border: 1px solid #ccc;
            border-radius: 10px;
        }
        label {
            display: block;
            margin-bottom: 5px;
        }
        input, select, textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .error {
            color: red;
            font-size: 12px;
            display: none;
        }
        button {
            padding: 10px 20px;
            background-color: green;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: darkgreen;
        }
        .thank-you {
            text-align: center;
            margin-top: 50px;
        }
        .thank-you img {
            width: 100px;
            height: 100px;
        }
    </style>
</head>
<body>

    <div class="form-container" id="formContainer">
        <h2>Shipping Form</h2>
        <form id="shippingForm">
            <label for="firstName">First Name:</label>
            <input type="text" id="firstName" name="firstName" placeholder="Enter your first name">
            <span class="error" id="firstNameError">Please enter your first name</span>

            <label for="lastName">Last Name:</label>
            <input type="text" id="lastName" name="lastName" placeholder="Enter your last name">
            <span class="error" id="lastNameError">Please enter your last name</span>

            <label for="streetAddress">Street Address:</label>
            <input type="text" id="streetAddress" name="streetAddress" placeholder="Enter your street address">
            <span class="error" id="addressError">Please enter your street address</span>

            <label for="city">City:</label>
            <input type="text" id="city" name="city" placeholder="Enter your city">
            <span class="error" id="cityError">Please enter your city</span>

            <label for="state">State:</label>
            <select id="state" name="state">
                <option value="">Select your state</option>
                <!-- US States -->
                <option value="AL">Alabama</option>
                <option value="AK">Alaska</option>
                <option value="AZ">Arizona</option>
                <option value="AR">Arkansas</option>
                <option value="CA">California</option>
                <option value="CO">Colorado</option>
                <option value="CT">Connecticut</option>
                <option value="DE">Delaware</option>
                <option value="FL">Florida</option>
                <option value="GA">Georgia</option>
                <option value="HI">Hawaii</option>
                <option value="ID">Idaho</option>
                <option value="IL">Illinois</option>
                <option value="IN">Indiana</option>
                <option value="IA">Iowa</option>
                <option value="KS">Kansas</option>
                <option value="KY">Kentucky</option>
                <option value="LA">Louisiana</option>
                <option value="ME">Maine</option>
                <option value="MD">Maryland</option>
                <option value="MA">Massachusetts</option>
                <option value="MI">Michigan</option>
                <option value="MN">Minnesota</option>
                <option value="MS">Mississippi</option>
                <option value="MO">Missouri</option>
                <option value="MT">Montana</option>
                <option value="NE">Nebraska</option>
                <option value="NV">Nevada</option>
                <option value="NH">New Hampshire</option>
                <option value="NJ">New Jersey</option>
                <option value="NM">New Mexico</option>
                <option value="NY">New York</option>
                <option value="NC">North Carolina</option>
                <option value="ND">North Dakota</option>
                <option value="OH">Ohio</option>
                <option value="OK">Oklahoma</option>
                <option value="OR">Oregon</option>
                <option value="PA">Pennsylvania</option>
                <option value="RI">Rhode Island</option>
                <option value="SC">South Carolina</option>
                <option value="SD">South Dakota</option>
                <option value="TN">Tennessee</option>
                <option value="TX">Texas</option>
                <option value="UT">Utah</option>
                <option value="VT">Vermont</option>
                <option value="VA">Virginia</option>
                <option value="WA">Washington</option>
                <option value="WV">West Virginia</option>
                <option value="WI">Wisconsin</option>
                <option value="WY">Wyoming</option>
            </select>
            <span class="error" id="stateError">Please select your state</span>

            <label for="country">Country:</label>
            <select id="country" name="country">
                <option value="">Select your country</option>
                <!-- List of Countries -->
                <option value="US">United States</option>
                <option value="CA">Canada</option>
                <option value="GB">United Kingdom</option>
                <option value="AU">Australia</option>
                <option value="IN">India</option>
                <option value="BR">Brazil</option>
                <option value="DE">Germany</option>
                <option value="FR">France</option>
                <option value="JP">Japan</option>
                <option value="CN">China</option>
                <option value="RU">Russia</option>
                <!-- Add all countries as needed -->
            </select>
            <span class="error" id="countryError">Please select your country</span>

            <label for="shippingMethod">Shipping Method:</label>
            <select id="shippingMethod" name="shippingMethod">
                <option value="">Select shipping method</option>
                <option value="standard">Standard</option>
                <option value="express">Express</option>
                <option value="overnight">Overnight</option>
            </select>
            <span class="error" id="shippingMethodError">Please select a shipping method</span>

            <button type="submit">Submit</button>
        </form>
    </div>

    <div class="thank-you" id="thankYouMessage" style="display: none;">
        <h2>Thank you for your order!</h2>
        <img src="https://via.placeholder.com/100?text=:)" alt="Happy face">
    </div>

    <script>
        document.getElementById('shippingForm').addEventListener('submit', function(event) {
            event.preventDefault();

            // Error checking
            let isValid = true;
            let errors = {
                firstName: document.getElementById('firstNameError'),
                lastName: document.getElementById('lastNameError'),
                address: document.getElementById('addressError'),
                city: document.getElementById('cityError'),
                state: document.getElementById('stateError'),
                country: document.getElementById('countryError'),
                shippingMethod: document.getElementById('shippingMethodError')
            };

            Object.keys(errors).forEach(function(field) {
                errors[field].style.display = 'none'; // Hide all errors initially
            });

            // Validate each field
            if (document.getElementById('firstName').value === '') {
                errors.firstName.style.display = 'block';
                isValid = false;
            }
            if (document.getElementById('lastName').value === '') {
                errors.lastName.style.display = 'block';
                isValid = false;
            }
            if (document.getElementById('streetAddress').value === '') {
                errors.address.style.display = 'block';
                isValid = false;
            }
            if (document.getElementById('city').value === '') {
                errors.city.style.display = 'block';
                isValid = false;
            }
            if (document.getElementById('state').value === '') {
                errors.state.style.display = 'block';
                isValid = false;
            }
            if (document.getElementById('country').value === '') {
                errors.country.style.display = 'block';
                isValid = false;
            }
            if (document.getElementById('shippingMethod').value === '') {
                errors.shippingMethod.style.display = 'block';
                isValid = false;
            }

            // If all fields are valid, show the thank you message
            if (isValid) {
                document.getElementById('formContainer').style.display = 'none';
                document.getElementById('thankYouMessage').style.display = 'block';
            }
        });
    </script>

</body>
</html>
