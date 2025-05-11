<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Form with Validation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
        }
        .form-container {
            max-width: 400px;
            margin: auto;
        }
        .input-group {
            margin-bottom: 10px;
        }
        .error {
            color: red;
            font-size: 12px;
        }
        .password-toggle {
            margin-top: 5px;
        }
    </style>
</head>
<body>

    <h2>Interactive Form</h2>
    <div class="form-container">
        <!-- Form Section -->
        <form id="myForm">
            <div class="input-group">
                <label for="username">Username:</label>
                <input type="text" id="username" name="username" required>
                <span class="error" id="usernameError"></span>
            </div>

            <div class="input-group">
                <label for="password">Password:</label>
                <input type="password" id="password" name="password" required>
                <button type="button" id="togglePassword" class="password-toggle">Show Password</button>
            </div>

            <button type="submit">Submit</button>
        </form>

        <div id="formResult"></div>
    </div>

    <script>
        // Event Listener for form submission
        document.getElementById('myForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent default form submission

            // Validate the form
            let username = document.getElementById('username').value;
            let password = document.getElementById('password').value;
            let usernameError = document.getElementById('usernameError');
            let formResult = document.getElementById('formResult');
            
            // Clear previous error messages
            usernameError.textContent = '';

            // Check if the username is empty
            if (username === '') {
                usernameError.textContent = 'Username cannot be empty!';
                return;
            }

            // If validation passes, show success message
            formResult.textContent = 'Form submitted successfully!';
            formResult.style.color = 'green';
        });

        // Toggle password visibility
        document.getElementById('togglePassword').addEventListener('click', function() {
            let passwordField = document.getElementById('password');
            if (passwordField.type === 'password') {
                passwordField.type = 'text';
                this.textContent = 'Hide Password';
            } else {
                passwordField.type = 'password';
                this.textContent = 'Show Password';
            }
        });
    </script>

</body>
</html>
