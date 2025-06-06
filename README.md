<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login & Signup Page</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .container {
            background: white;
            border-radius: 10px;
            box-shadow: 0 14px 28px rgba(0,0,0,0.25), 
                        0 10px 10px rgba(0,0,0,0.22);
            position: relative;
            overflow: hidden;
            width: 768px;
            max-width: 100%;
            min-height: 480px;
        }
        
        .form-container {
            position: absolute;
            top: 0;
            height: 100%;
            transition: all 0.6s ease-in-out;
        }
        
        .sign-in-container {
            left: 0;
            width: 50%;
            z-index: 2;
        }
        
        .container.right-panel-active .sign-in-container {
            transform: translateX(100%);
        }
        
        .sign-up-container {
            left: 0;
            width: 50%;
            opacity: 0;
            z-index: 1;
        }
        
        .container.right-panel-active .sign-up-container {
            transform: translateX(100%);
            opacity: 1;
            z-index: 5;
            animation: show 0.6s;
        }
        
        @keyframes show {
            0%, 49.99% {
                opacity: 0;
                z-index: 1;
            }
            
            50%, 100% {
                opacity: 1;
                z-index: 5;
            }
        }
        
        .overlay-container {
            position: absolute;
            top: 0;
            left: 50%;
            width: 50%;
            height: 100%;
            overflow: hidden;
            transition: transform 0.6s ease-in-out;
            z-index: 100;
        }
        
        .container.right-panel-active .overlay-container {
            transform: translateX(-100%);
        }
        
        .overlay {
            background: linear-gradient(to right, #ff4b2b, #ff416c);
            background-repeat: no-repeat;
            background-size: cover;
            background-position: 0 0;
            color: #ffffff;
            position: relative;
            left: -100%;
            height: 100%;
            width: 200%;
            transform: translateX(0);
            transition: transform 0.6s ease-in-out;
        }
        
        .container.right-panel-active .overlay {
            transform: translateX(50%);
        }
        
        .overlay-panel {
            position: absolute;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            padding: 0 40px;
            text-align: center;
            top: 0;
            height: 100%;
            width: 50%;
            transform: translateX(0);
            transition: transform 0.6s ease-in-out;
        }
        
        .overlay-left {
            transform: translateX(-20%);
        }
        
        .container.right-panel-active .overlay-left {
            transform: translateX(0);
        }
        
        .overlay-right {
            right: 0;
            transform: translateX(0);
        }
        
        .container.right-panel-active .overlay-right {
            transform: translateX(20%);
        }
        
        h1 {
            font-weight: bold;
            margin: 0;
        }
        
        p {
            font-size: 14px;
            font-weight: 100;
            line-height: 20px;
            letter-spacing: 0.5px;
            margin: 20px 0 30px;
        }
        
        span {
            font-size: 12px;
        }
        
        a {
            color: #333;
            font-size: 14px;
            text-decoration: none;
            margin: 15px 0;
        }
        
        button {
            border-radius: 20px;
            border: 1px solid #ff4b2b;
            background: #ff4b2b;
            color: #ffffff;
            font-size: 12px;
            font-weight: bold;
            padding: 12px 45px;
            letter-spacing: 1px;
            text-transform: uppercase;
            transition: transform 80ms ease-in;
            cursor: pointer;
        }
        
        button:active {
            transform: scale(0.95);
        }
        
        button:focus {
            outline: none;
        }
        
        button.ghost {
            background: transparent;
            border-color: #ffffff;
        }
        
        form {
            background: #ffffff;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            padding: 0 50px;
            height: 100%;
            text-align: center;
        }
        
        input {
            background: #eee;
            border: none;
            padding: 12px 15px;
            margin: 8px 0;
            width: 100%;
            border-radius: 5px;
        }
        
        .social-container {
            margin: 20px 0;
        }
        
        .social-container a {
            border: 1px solid #dddddd;
            border-radius: 50%;
            display: inline-flex;
            justify-content: center;
            align-items: center;
            margin: 0 5px;
            height: 40px;
            width: 40px;
        }
        
        .error {
            color: red;
            font-size: 12px;
            margin-top: -5px;
            margin-bottom: 10px;
            display: none;
        }
        
        .success {
            color: green;
            font-size: 12px;
            margin-top: -5px;
            margin-bottom: 10px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container" id="container">
        <div class="form-container sign-up-container">
            <form action="#" id="signupForm">
                <h1>Create Account</h1>
                <div class="social-container">
                    <a href="#" class="social"><i class="fab fa-facebook-f"></i></a>
                    <a href="#" class="social"><i class="fab fa-google-plus-g"></i></a>
                    <a href="#" class="social"><i class="fab fa-linkedin-in"></i></a>
                </div>
                <span>or use your email for registration</span>
                <input type="text" placeholder="Name" id="signupName" required />
                <input type="email" placeholder="Email" id="signupEmail" required />
                <input type="password" placeholder="Password" id="signupPassword" required />
                <input type="password" placeholder="Confirm Password" id="signupConfirmPassword" required />
                <div class="error" id="signupError"></div>
                <div class="success" id="signupSuccess"></div>
                <button type="submit">Sign Up</button>
            </form>
        </div>
        <div class="form-container sign-in-container">
            <form action="#" id="loginForm">
                <h1>Sign in</h1>
                <div class="social-container">
                    <a href="#" class="social"><i class="fab fa-facebook-f"></i></a>
                    <a href="#" class="social"><i class="fab fa-google-plus-g"></i></a>
                    <a href="#" class="social"><i class="fab fa-linkedin-in"></i></a>
                </div>
                <span>or use your account</span>
                <input type="email" placeholder="Email" id="loginEmail" required />
                <input type="password" placeholder="Password" id="loginPassword" required />
                <div class="error" id="loginError"></div>
                <div class="success" id="loginSuccess"></div>
                <a href="#">Forgot your password?</a>
                <button type="submit">Sign In</button>
            </form>
        </div>
        <div class="overlay-container">
            <div class="overlay">
                <div class="overlay-panel overlay-left">
                    <h1>Welcome Back!</h1>
                    <p>To keep connected with us please login with your personal info</p>
                    <button class="ghost" id="signIn">Sign In</button>
                </div>
                <div class="overlay-panel overlay-right">
                    <h1>Hello, Friend!</h1>
                    <p>Enter your personal details and start journey with us</p>
                    <button class="ghost" id="signUp">Sign Up</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Toggle between sign in and sign up forms
        const signUpButton = document.getElementById('signUp');
        const signInButton = document.getElementById('signIn');
        const container = document.getElementById('container');

        signUpButton.addEventListener('click', () => {
            container.classList.add('right-panel-active');
        });

        signInButton.addEventListener('click', () => {
            container.classList.remove('right-panel-active');
        });

        // Store users in localStorage
        let users = JSON.parse(localStorage.getItem('users')) || [];

        // Form elements
        const signupForm = document.getElementById('signupForm');
        const loginForm = document.getElementById('loginForm');
        const signupError = document.getElementById('signupError');
        const signupSuccess = document.getElementById('signupSuccess');
        const loginError = document.getElementById('loginError');
        const loginSuccess = document.getElementById('loginSuccess');

        // Signup form validation
        signupForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            const name = document.getElementById('signupName').value.trim();
            const email = document.getElementById('signupEmail').value.trim().toLowerCase();
            const password = document.getElementById('signupPassword').value;
            const confirmPassword = document.getElementById('signupConfirmPassword').value;
            
            // Clear previous messages
            signupError.style.display = 'none';
            signupSuccess.style.display = 'none';
            
            // Validation checks
            if (!name || !email || !password || !confirmPassword) {
                showError(signupError, "All fields are required!");
                return;
            }
            
            if (password !== confirmPassword) {
                showError(signupError, "Passwords don't match!");
                return;
            }
            
            if (password.length < 6) {
                showError(signupError, "Password must be at least 6 characters!");
                return;
            }
            
            // Check if email already exists
            const emailExists = users.some(user => user.email === email);
            if (emailExists) {
                showError(signupError, "This email is already registered!");
                return;
            }
            
            // Check if username already exists
            const nameExists = users.some(user => user.name.toLowerCase() === name.toLowerCase());
            if (nameExists) {
                showError(signupError, "This username is already taken!");
                return;
            }
            
            // If all validations pass, create new user
            const newUser = {
                name: name,
                email: email,
                password: password // Note: In real app, hash the password
            };
            
            users.push(newUser);
            localStorage.setItem('users', JSON.stringify(users));
            
            showSuccess(signupSuccess, "Sign up successful! You can now login.");
            signupForm.reset();
            
            // Auto switch to login after 2 seconds
            setTimeout(() => {
                container.classList.remove('right-panel-active');
            }, 2000);
        });

        // Login form validation
        loginForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            const email = document.getElementById('loginEmail').value.trim().toLowerCase();
            const password = document.getElementById('loginPassword').value;
            
            // Clear previous messages
            loginError.style.display = 'none';
            loginSuccess.style.display = 'none';
            
            // Validation checks
            if (!email || !password) {
                showError(loginError, "Please fill in all fields!");
                return;
            }
            
            // Check if user exists and credentials match
            const user = users.find(user => user.email === email);
            
            if (!user) {
                showError(loginError, "No account found with this email!");
                return;
            }
            
            if (user.password !== password) {
                showError(loginError, "Incorrect password!");
                return;
            }
            
            // If validation passes
            showSuccess(loginSuccess, `Welcome back, ${user.name}!`);
            loginForm.reset();
        });

        // Helper functions
        function showError(element, message) {
            element.textContent = message;
            element.style.display = 'block';
        }

        function showSuccess(element, message) {
            element.textContent = message;
            element.style.display = 'block';
        }
    </script>
</body>
</html>
