# RegistrationForm1
HTML

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registration Form</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <div class="container">
        <h1>Registration Form</h1>
        <form id="registration-form">
            <label for="name">Full Name:</label>
            <input type="text" id="name" name="name" placeholder="Enter your full name" required>

            <label for="email">Email:</label>
            <input type="email" id="email" name="email" placeholder="Enter your email" required>

            <label for="password">Password:</label>
            <input type="password" id="password" name="password" placeholder="Create a password" required>

            <label for="confirm-password">Confirm Password:</label>
            <input type="password" id="confirm-password" name="confirm-password" placeholder="Confirm your password" required>

            <button type="submit">Register</button>
        </form>
        <div id="message"></div>
    </div>

    <script src="script.js"></script>
</body>
</html>



CSS

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container {
    background-color: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 400px;
}

h1 {
    text-align: center;
    color: #333;
}

form {
    display: flex;
    flex-direction: column;
}

label {
    margin: 10px 0 5px;
    color: #555;
}

input {
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 10px;
    background-color: #5cb85c;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #4cae4c;
}

#message {
    margin-top: 10px;
    text-align: center;
}

.error {
    color: red;
}

.success {
    color: green;
}



Javascript

document.getElementById('registration-form').addEventListener('submit', function(event) {
    event.preventDefault();

    const name = document.getElementById('name').value;
    const email = document.getElementById('email').value;
    const password = document.getElementById('password').value;
    const confirmPassword = document.getElementById('confirm-password').value;

    const messageElement = document.getElementById('message');

    if (password !== confirmPassword) {
        messageElement.textContent = 'Passwords do not match!';
        messageElement.className = 'error';
        return;
    }

    const user = {
        name: name,
        email: email,
        password: password
    };

    // Store user information in local storage (for demonstration purposes)
    localStorage.setItem('user', JSON.stringify(user));

    messageElement.textContent = 'Registration successful!';
    messageElement.className = 'success';

    // Optionally clear the form
    document.getElementById('registration-form').reset();
});
