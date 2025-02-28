# PHP Login and Registration System

## Overview
This project is a simple PHP-based login and registration system with session handling and basic user authentication. User data (email, password, and username) is stored in a session array, and passwords are hashed using the MD5 algorithm.

## Features
- User registration with email, password, and name.
- User login with email and password.
- Password hashing for security.
- Session management to store user data.
- Basic error handling and validation.

## File Structure
- **index.php**: Handles user login and redirects to the welcome page on successful login.
- **register.php**: Handles user registration and checks for duplicate emails.
- **UserData.php**: Defines and initializes user data.
- **style.css**: Contains styles for the login and registration forms.
- **Welcome.php**: The landing page after successful login.

## How It Works
### Registration
1. User enters their name, email, and password in `register.php`.
2. The `Register()` function checks if the email already exists in the session array.
3. If the email is unique, the email and password are hashed using MD5 and stored in the session array.
4. On success, the user is redirected to the login page (`index.php`).
5. If the email exists, an error message is displayed.

### Login
1. User enters their email and password on `index.php`.
2. The `Login()` function compares the hashed email and password with the session array.
3. If credentials match, the user is redirected to `Welcome.php`.
4. If they don’t match, an error message is shown.

## User Data
The user data is stored in a session array:
```
$_SESSION['Array'] = array(
    array(md5(email), md5(password), username)
);
```

## Security Note
- Passwords are currently hashed using MD5, which is outdated and insecure. Consider using a more secure algorithm like bcrypt or Argon2.
- This system doesn’t use a database — user data is stored in session, meaning it’s temporary and resets when the session ends.

## Setup
1. Ensure your server supports PHP sessions.
2. Start the session at the top of each PHP file with `session_start()`.
3. Run `index.php` for login and `register.php` for registration.

## Future Improvements
- Use a database (like MySQL) for permanent user storage.
- Replace MD5 hashing with a more secure hashing method.
- Implement user logout functionality.
- Add input validation and sanitation to prevent XSS and SQL injection.

