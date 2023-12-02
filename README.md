<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page with IP</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            background: url('https://raw.githubusercontent.com/Rexn399/Ff/d5c17308cdc7c0883897d7de20fc44468755e61c/47%20Sem%20T%C3%ADtulo_20231202113827.png') center/cover no-repeat fixed;
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: white;
        }

        #clickMeButton {
            width: 100px;
            height: 100px;
            background-color: darkgray;
            color: red;
            border: none;
            cursor: pointer;
            font-size: 20px;
        }

        #ipDisplay {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            text-align: center;
            width: 80%;
            max-width: 400px;
            background: rgba(0, 0, 0, 0.7);
            padding: 20px;
            color: red;
        }
    </style>
</head>
<body>
    <button id="clickMeButton" onclick="showInformation()">Click Me</button>

    <div id="ipDisplay">
        <p id="ipText">Your IP address is:</p>
        <p id="userAgent"></p>
    </div>

    <script>
        async function getIpAddress() {
            try {
                const response = await fetch('https://ipinfo.io/json');
                const data = await response.json();
                return data;
            } catch (error) {
                console.error('Error getting IP address:', error.message);
                return { ip: 'Unavailable' };
            }
        }

        function showInformation() {
            getIpAddress().then(data => {
                const ipAddress = data.ip;
                const userAgent = navigator.userAgent;

                document.getElementById('ipText').textContent = `Your IP address is: ${ipAddress}`;
                document.getElementById('userAgent').textContent = `User Agent: ${userAgent}`;
                document.getElementById('ipDisplay').style.display = 'block';
            });
        }
    </script>
</body>
</html>
