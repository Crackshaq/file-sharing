<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>File Sharing Platform</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #2c3e50, #bdc3c7);
            color: #333;
        }
        .container {
            max-width: 800px;
            margin: 50px auto;
            padding: 20px;
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        .login-container, .file-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        h1 {
            color: #2c3e50;
        }
        .form-group {
            margin: 10px 0;
            width: 100%;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        .form-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .form-group button {
            width: 100%;
            padding: 10px;
            background: #3498db;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .form-group button:hover {
            background: #2980b9;
        }
        .logout-btn {
            margin: 10px 0;
            padding: 10px 20px;
            background: #e74c3c;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .logout-btn:hover {
            background: #c0392b;
        }
        .file-list {
            list-style: none;
            padding: 0;
        }
        .file-list li {
            margin: 10px 0;
            background: #f1f1f1;
            padding: 10px;
            border-radius: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .file-list li a {
            text-decoration: none;
            color: #3498db;
        }
        .file-list li a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="container login-container" id="login-container">
        <h1>Login</h1>
        <form id="login-form">
            <div class="form-group">
                <label for="username">Username:</label>
                <input type="text" id="username" name="username" required>
            </div>
            <div class="form-group">
                <label for="password">Password:</label>
                <input type="password" id="password" name="password" required>
            </div>
            <div class="form-group">
                <button type="submit">Login</button>
            </div>
        </form>
    </div>

    <div class="container file-container" id="file-container" style="display: none;">
        <h1>File Sharing Platform</h1>
        <button class="logout-btn" id="logout-btn">Logout</button>
        <form id="upload-form">
            <div class="form-group">
                <label for="file">Upload File:</label>
                <input type="file" id="file" name="file" required>
            </div>
            <div class="form-group">
                <button type="submit">Upload</button>
            </div>
        </form>
        <ul class="file-list" id="file-list">
            <!-- File items will appear here -->
        </ul>
    </div>

    <script>
        const loginContainer = document.getElementById('login-container');
        const fileContainer = document.getElementById('file-container');
        const loginForm = document.getElementById('login-form');
        const uploadForm = document.getElementById('upload-form');
        const fileList = document.getElementById('file-list');
        const logoutBtn = document.getElementById('logout-btn');

        loginForm.addEventListener('submit', (e) => {
            e.preventDefault();
            // Simple authentication (For demonstration purposes only)
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            if (username === 'sai' && password === 'saicharan') {
                loginContainer.style.display = 'none';
                fileContainer.style.display = 'block';
            } else {
                alert('Invalid username or password');
            }
        });

        uploadForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const fileInput = document.getElementById('file');
            const file = fileInput.files[0];
            if (file) {
                const listItem = document.createElement('li');
                listItem.innerHTML = `${file.name} <a href="#">Download</a>`;
                fileList.appendChild(listItem);
            }
        });

        logoutBtn.addEventListener('click', () => {
            fileContainer.style.display = 'none';
            loginContainer.style.display = 'block';
        });
    </script>
</body>
</html>
