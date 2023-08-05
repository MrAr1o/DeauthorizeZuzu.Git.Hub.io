# DeauthorizeZuzu.Git.Hub.io
<!DOCTYPE html>
<html>
<head>
    <title>Deauthorize Callback URL</title>
</head>
<body>
    <h1>Deauthorize Callback URL</h1>
    <form id="deauthForm">
        <label for="deauthUrl">Deauthorize Callback URL:</label>
        <input type="url" id="deauthUrl" name="deauthUrl" placeholder="Enter Deauthorize Callback URL" required>
        <button type="submit">Submit</button>
    </form>
    <div id="resultContainer">
        <p>Deauthorize Callback URL:</p>
        <p id="displayDeauthUrl">Not provided</p>
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
