# task3MainFLow

#html code

<!DOCTYPE html>
<html>
<head>
    <title>Registration Form</title>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>

    <header>
        <h1>Main <span class="flow">Flow</span></h1>
    </header>

    <div class="container">
        <div class="form-container">
            <h2>Registration Form</h2>
            <form id="registrationForm" action="submit_registration.php" method="post">
                <label for="name">Name</label>
                <input type="text" id="name" name="name" required>

                <label for="email">Email</label>
                <input type="email" id="email" name="email" required>

                <label for="password">Password</label>
                <input type="password" id="password" name="password" required>

                <label for="phone">Phone Number</label>
                <input type="tel" id="phone" name="phone" required>

                <input type="submit" value="Submit">
            </form>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>


#csscode

body {
    background-color: #f0f0f0; 
    color: #333; 
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    flex-direction: column;
}

header {
    width: 100%;
    background-color: #333; 
    color: white; 
    text-align: left;
    padding: 20px;
    box-sizing: border-box;
}

header h1 {
    font-size: 2em;
    margin: 0;
}

header .flow {
    color: #00d1b2;
}

.container {
    text-align: center;
    flex-grow: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
}

.form-container {
    background-color: #2a2a2a; 
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
    width: 350px;
    margin: 0 auto;
    text-align: left;
}

.form-container h2 {
    margin-bottom: 20px;
    font-size: 1.5em;
    color: white; 
    text-align: center;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
    color: white; 
}

input[type="text"], input[type="email"], input[type="password"], input[type="tel"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #00d1b2;
    border-radius: 4px;
    background-color: #1c1c1c;
    color: #fff;
    box-sizing: border-box;
}

input[type="submit"] {
    width: 100%;
    padding: 10px;
    background-color: #00d1b2;
    border: none;
    border-radius: 4px;
    color: white;
    font-size: 16px;
    cursor: pointer;
    margin-top: 10px;
}

input[type="submit"]:hover {
    background-color: #00a899;
}



#js code

document.getElementById('registrationForm').addEventListener('submit', function(event) {

    event.preventDefault();


    const name = document.getElementById('name').value;
    const email = document.getElementById('email').value;
    const password = document.getElementById('password').value;
    const phone = document.getElementById('phone').value;

  
    const sanitizedData = {
        name: sanitizeInput(name),
        email: sanitizeInput(email),
        password: sanitizeInput(password),
        phone: sanitizeInput(phone)
    };


    if (!isValidEmail(sanitizedData.email)) {
        alert('Please enter a valid email address.');
        return;
    }

   
    console.log('Form submitted with data:', sanitizedData);
});

function sanitizeInput(input) {
    const tempElement = document.createElement('div');
    tempElement.textContent = input;
    return tempElement.innerHTML;
}

function isValidEmail(email) {

    const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return emailPattern.test(email);
}




