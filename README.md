//HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Website</title>
    <link rel="stylesheet" href="newstyle.css">
</head>
<body>
    
    <div class="index index-container">
        <h1 class="index-class">Welcome to Simple Website</h1>
        <button onclick="toggle_login()" class="index-button">Login</button>
        <button onclick="toggle_signup()" class="index-button">Sign up</button>
    </div>
    <div class="login-page" style="display: none;">
        <h1>Login</h1>
        <form id="loginForm">
            <div class="form-group">
                <label for="username">Username:</label>
                <input type="text" id="username" name="username" placeholder="Enter your username" autocomplete="off" required>
            </div>
            <div class="form-group">
                <label for="password">Password:</label>
                <input type="password" id="password" name="password" placeholder="Enter your password" autocomplete="new-password" required>
            </div>
            <button class="button" type="submit" onclick="login()">Login</button>
            <p>Don't have an account? <a href="#" onclick="toggle_signup()">Sign Up</a></p>
        </form>
    </div>
    <div class = "signup-page" style="display: none;">
        <h1>Sign Up</h1>
        <form id="signupForm">
            <div class="form-group">
                <label for="username">Username:</label>
                <input type="text" id="newUsername" name="username" placeholder="Enter your username" autocomplete="off" required>
            </div>
            <div class="form-group">
                <label for="password">Password:</label>
                <input type="password" id="newPassword" name="password" placeholder="Enter your password" autocomplete="new-password" required>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="newEmail" name="email" placeholder="Enter your email" autocomplete="off" required>
            </div>
            <div class="form-group">
                <label for="age">age:</label>
                <input type="number" id="newAge" name="age" placeholder="Enter your age" autocomplete="off" required>
            </div>
            <div class="form-group">
                <label for="gender">gender:</label>
                <input type="text" id="newGender" name="gender" placeholder="Enter your gender" autocomplete="off" required>
            </div>
            <div class="form-group">
                <label for="weight">weight:</label>
                <input type="number" id="newWeight" name="weight" placeholder="Enter your weight" autocomplete="off" required>
            </div>
            <div class="form-group">
                <label for="height">height:</label>
                <input type="number" id="newHeight" name="height" placeholder="Enter your height" autocomplete="off" required>
            </div>
            <button type="submit" onclick="signup()">Sign Up</button>
            <p>Already have an account? <a href="#" onclick="toggle_login()">Login</a></p>
        </form>
    </div>
    <div class="home-page" style="display: none;">
        <h1>Welcome to your Home Page, <span id="welcomeUser"></span>!</h1>
        <div id="userInfo">
            <h2>User Information</h2>
            <p><strong>Username:</strong> <span id="userUsername"></span></p>
            <p><strong>Password:</strong> <span id="userPassword"></span></p>
            <p><strong>Email:</strong> <span id="userEmail"></span></p>
            <p><strong>Age:</strong> <span id="userAge"></span></p>
            <p><strong>Gender:</strong> <span id="userGender"></span></p>
            <p><strong>Weight:</strong> <span id="userWeight"></span></p>
            <p><strong>Height:</strong> <span id="userHeight"></span></p>
            <p><strong>Disease:</strong> <span id="userDisease"></span></p>
            <p><strong>check Symptomps:</strong> <span id="userSymptomps"></span></p>

        </div>
        <button onclick="editProfile()">Edit Profile</button>
        <button onclick="logout()">Logout</button>
    </div>
    <script src="script.js"></script>
</body>
</html>





//CSS
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

.index-container {
    max-width: 400px;
    margin: 100px auto;
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    text-align: center;
}

.index-h1 {
    margin-bottom: 20px;
}

.index-options {
    display: flex;
    justify-content: center;
}

.index-button {
    display: inline-block;
    padding: 10px 20px;
    background-color: #007bff;
    color: #fff;
    text-decoration: none;
    border-radius: 4px;
    margin: 0 10px;
    border: none;
    cursor: pointer;
}

.index-button:hover {
    background-color: #0056b3;
}


.container {
    max-width: 400px;
    margin: 100px auto;
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
}

.form-group {
    margin-bottom: 20px;
}

label {
    display: block;
    font-weight: bold;
}

input[type="text"],
input[type="password"] {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

button {
    display: block;
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

p {
    text-align: center;
}

a {
    color: #007bff;
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}





//JAVASCRIPT
let currentUser = null;
let users = [];

function login() {
    // window.location.href = "login.html";
    // const users = JSON.parse(localStorage.getItem('users')) || [];
    const username = document.getElementById('username').value;
    const password = document.getElementById('password').value;

    // Here you would typically send a request to your server to authenticate the user
    // For simplicity, we'll just check if the username and password match
    const user = users.find(user => user.username === username && user.password === password);
    clearForm();
    if (user) {
        currentUser = username;
        alert(`Welcome back, ${username}!`);
        toggle_home(currentUser, user.password, user.email, user.age, user.gender, user.weight, user.height);
        // window.href.location = "home.html";
    } else {
        alert('Invalid username or password.');
    }
}

function signup() {
    // alert('Signup feature is not implemented yet.');
    // const users = JSON.parse(localStorage.getItem('users')) || [];
    const newUsername = document.getElementById('newUsername').value;
    const newPassword = document.getElementById('newPassword').value;
    const newEmail = document.getElementById('newEmail').value;
    const newAge = document.getElementById('newAge').value;
    const newGender = document.getElementById('newGender').value;
    const newWeight = document.getElementById('newWeight').value;
    const newHeight = document.getElementById('newHeight').value;
    
    if (users.some(user => user.username === newUsername)) {
        alert('Username already exists. Please choose a different one.');
        return;
    }
    
    users.push({ username: newUsername, password: newPassword, email: newEmail, age: newAge, gender: newGender, weight: newWeight, height: newHeight});
    // localStorage.setItem('users', JSON.stringify(users));
    alert(`New Account Created\nUsername: ${newUsername}\nPassword: ${newPassword}`);
    // window.location.href = "signup.html";
    // print the user array
    // console.log(users);
    clearForm();
    toggle_login();
}

function toggle_index() {
    document.querySelector('.index').style.display = 'block';
    document.querySelector('.signup-page').style.display = 'none';
    document.querySelector('.home-page').style.display = 'none';
    document.querySelector('.login-page').style.display = 'none';
}

function toggle_login() {
    document.querySelector('.index').style.display = 'none';
    document.querySelector('.signup-page').style.display = 'none';
    document.querySelector('.home-page').style.display = 'none';
    document.querySelector('.login-page').style.display = 'block';
}

function toggle_signup() {
    document.querySelector('.index').style.display = 'none';
    document.querySelector('.login-page').style.display = 'none';
    document.querySelector('.home-page').style.display = 'none';
    document.querySelector('.signup-page').style.display = 'block';
}

// Add more functions to toggle other sections as needed (e.g., toggleHome())

// Function to show home page after successful login
function toggle_home(username, password, email, age, gender, weight, height) {
    document.querySelector('.index').style.display = 'none';
    document.querySelector('.login-page').style.display = 'none';
    document.querySelector('.signup-page').style.display = 'none';
    document.querySelector('.home-page').style.display = 'block';
    document.getElementById('welcomeUser').innerText = username;
    document.getElementById('userUsername').innerText = username;
    document.getElementById('userPassword').innerText = password;
    document.getElementById('userEmail').innerText = email;
    document.getElementById('userAge').innerText = age;
    document.getElementById('userGender').innerText = gender;
    document.getElementById('userWeight').innerText = weight;
    document.getElementById('userHeight').innerText = height;
    document.getElementById('userDisease').innerText = "None";
    document.getElementById('userHeight').innerText = "Not applicable";
}

function logout() {
    currentUser = null;
    toggle_index();
}


function editProfile() {
    const newPassword = prompt('Enter your new password:');
    const newEmail = prompt('Enter your new email:');
    const newAge = prompt('Enter your new age:');
    const newGender = prompt('Enter your new gender:');
    const newWeight = prompt('Enter your new weight:');
    const newHeight = prompt('Enter your new height:');


    if (newEmail || newPassword || newAge || newGender || newWeight || newHeight) {
        // Update the user's profile in the users array
        const index = users.findIndex(user => user.username === currentUser);
        if (newEmail) {
            users[index].email = newEmail;
            // Update displayed email
            document.getElementById('userEmail').textContent = newEmail;
        }
        if (newPassword) {
            users[index].password = newPassword;
            // Update displayed password
            document.getElementById('userPassword').textContent = newPassword;
        }
        if (newAge) {
            users[index].age = newAge;
            // Update displayed age
            document.getElementById('userAge').textContent = newAge;
        }
        if (newGender) {
            users[index].gender = newGender;
            // Update displayed gender
            document.getElementById('userGender').textContent = newGender;
        }
        if (newWeight) {
            users[index].weight = newWeight;
            // Update displayed weight
            document.getElementById('userWeight').textContent = newWeight;
        }
        if (newHeight) {
            users[index].height = newHeight;
            // Update displayed height
            document.getElementById('userHeight').textContent = newHeight;
        }

        localStorage.setItem('users', JSON.stringify(users));
        alert('Profile updated successfully!');
        toggle_home(currentUser, newPassword, newEmail, newAge, newGender, newWeight, newHeight);
    } else {
        alert('No changes made to the profile.');
    }
}

function clearForm() {
    // Get all input elements in the form
    var formInputs = document.querySelectorAll('input');

    // Loop through each input element and set its value to an empty string
    formInputs.forEach(function(input) {
        input.value = '';
    });
}










