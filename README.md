<!DOCTYPE html>
<html>
<head>
    <title>Deauthorize Callback URL</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f9f9f9;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        h1 {
            text-align: center;
            color: #333;
            font-size: 36px;
            margin-bottom: 20px;
        }

        #deauthForm {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            background-color: #fff;
            max-width: 400px;
        }

        label {
            font-size: 18px;
            margin-bottom: 5px;
        }

        input {
            padding: 8px;
            font-size: 16px;
            border: 1px solid #ccc;
            border-radius: 4px;
            width: 100%;
            margin-bottom: 15px;
        }

        button {
            background-color: #007bff;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }

        #resultContainer {
            margin-top: 20px;
            display: none;
        }

        #resultContainer p {
            font-size: 18px;
        }

        #resultContainer span {
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>Deauthorize Callback URL</h1>
    <form id="deauthForm">
        <label for="deauthUrl">Deauthorize Callback URL:</label>
        <input type="url" id="deauthUrl" name="deauthUrl" placeholder="Enter Deauthorize Callback URL" required>
        <button type="submit">Submit</button>
    </form>
    <div id="resultContainer">
        <p>Deauthorize Callback URL: <span id="displayDeauthUrl">Not provided</span></p>
    </div>

    <script>
        const deauthForm = document.getElementById('deauthForm');
        const displayDeauthUrlSpan = document.getElementById('displayDeauthUrl');
        const resultContainer = document.getElementById('resultContainer');

        deauthForm.addEventListener('submit', function(event) {
            event.preventDefault();
            const deauthUrlInput = document.getElementById('deauthUrl');
            const deauthUrl = deauthUrlInput.value.trim();

            // Check if the input is not empty and is a valid URL
            if (deauthUrl !== '' && isValidUrl(deauthUrl)) {
                displayDeauthUrlSpan.textContent = deauthUrl;
                resultContainer.style.display = 'block';
            } else {
                // Show an error message if the input is invalid
                deauthUrlInput.setCustomValidity('Please enter a valid URL');
                deauthUrlInput.reportValidity();
            }
        });

        // Function to validate URL format
        function isValidUrl(url) {
            try {
                new URL(url);
                return true;
            } catch (error) {
                return false;
            }
        }
    </script>
</body>
</html>

