# Example 1 — Create a Login Page

This example shows the full input → output mapping for a greenfield login page in a local project folder.

---

## Input

| Field | Value |
|-------|-------|
| **Ticket name** | Createa login page |
| **Description** | I want a login page implement a login page with javascript and html |
| **Project URL** | `/Users/israel.caceres/Documents/lanchain-course/login_page` |
| **Assigned to** | Israel |

**Implicit acceptance criterion (from description / standard UI expectations):**
- The login page should be responsive

---

## Expected output

### Ticket name
Create a login page

### Description
I want a login page. Implement a login page with JavaScript and HTML.

### Time estimate
3

### Acceptance criteria
- The login page should be responsive
- The page includes email and password fields with client-side validation
- Form submission is handled in JavaScript without a full page reload

### Assigned to
Israel

### Suggested changes

Apply the following changes to `/Users/israel.caceres/Documents/lanchain-course/login_page/login.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Secure Login</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: #f0f2f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .login-container {
            background: #ffffff;
            padding: 40px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 400px;
        }

        .login-container h2 {
            margin-bottom: 24px;
            color: #333333;
            text-align: center;
        }

        .input-group {
            margin-bottom: 20px;
        }

        .input-group label {
            display: block;
            margin-bottom: 8px;
            color: #666666;
            font-size: 14px;
        }

        .input-group input {
            width: 100%;
            padding: 12px;
            border: 1px solid #cccccc;
            border-radius: 4px;
            font-size: 16px;
            outline: none;
            transition: border-color 0.2s;
        }

        .input-group input:focus {
            border-color: #0066cc;
        }

        .error-message {
            color: #ff3333;
            font-size: 12px;
            margin-top: 5px;
            min-height: 18px;
        }

        .login-btn {
            width: 100%;
            padding: 12px;
            background-color: #0066cc;
            border: none;
            border-radius: 4px;
            color: white;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .login-btn:hover {
            background-color: #0052a3;
        }
    </style>
</head>
<body>

<div class="login-container">
    <h2>Welcome Back</h2>
    <form id="loginForm">
        <div class="input-group">
            <label for="email">Email Address</label>
            <input type="email" id="email" autocomplete="username">
            <div class="error-message" id="emailError"></div>
        </div>

        <div class="input-group">
            <label for="password">Password</label>
            <input type="password" id="password" autocomplete="current-password">
            <div class="error-message" id="passwordError"></div>
        </div>

        <button type="submit" class="login-btn">Log In</button>
    </form>
</div>

<script>
    document.getElementById('loginForm').addEventListener('submit', function(event) {
        event.preventDefault();

        const email = document.getElementById('email').value.trim();
        const password = document.getElementById('password').value.trim();

        const emailError = document.getElementById('emailError');
        const passwordError = document.getElementById('passwordError');

        emailError.textContent = '';
        passwordError.textContent = '';

        let isValid = true;

        if (!email) {
            emailError.textContent = 'Email is required.';
            isValid = false;
        } else if (!validateEmail(email)) {
            emailError.textContent = 'Please enter a valid email address.';
            isValid = false;
        }

        if (!password) {
            passwordError.textContent = 'Password is required.';
            isValid = false;
        } else if (password.length < 6) {
            passwordError.textContent = 'Password must be at least 6 characters.';
            isValid = false;
        }

        if (isValid) {
            console.log('Form submitted successfully!');
            console.log('Email:', email);
            alert('Login successful! (Simulated)');
        }
    });

    function validateEmail(email) {
        const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return re.test(String(email).toLowerCase());
    }
</script>

</body>
</html>
```

---

## Mapping notes (for the AI)

| Input → Output | Rule applied |
|----------------|--------------|
| `Createa login page` → `Create a login page` | Fix typo in ticket name only |
| Description kept similar | Preserve user intent; light punctuation cleanup |
| No time in input → `3` | Small greenfield HTML/JS page heuristic |
| Responsive AC | Explicit user expectation + viewport/flex CSS in suggested file |
| Empty project folder | Single new file `login.html` with full content |
| `Israel` → Assigned to | Pass through optional field |

---

## Why this example matters

- Demonstrates **Project URL** pointing to a **local path**, not a Git remote.
- Shows **suggested changes** as a complete implementable file.
- Shows how **acceptance criteria** can start from one user line and expand slightly for testability.
- Serves as the **reference pattern** for similar frontend feature tickets.
