<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StreamElements Subcount for xtlos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
            background-color: #f4f4f9;
        }
        h1 {
            color: #6441a5;
        }
        #subcount {
            font-size: 2rem;
            font-weight: bold;
            color: #333;
        }
    </style>
</head>
<body>
    <h1>Subcount for Twitch User: xtlos</h1>
    <div id="subcount">Loading...</div>

    <script>
        const channelName = 'xtlos';  // Set the Twitch username here
        const accessToken = 'YOUR_ACCESS_TOKEN';  // Replace with your StreamElements access token

        async function getSubcount() {
            try {
                const response = await fetch(`https://api.streamelements.com/kappa/v2/subs/${channelName}`, {
                    method: 'GET',
                    headers: {
                        'Authorization': `Bearer ${accessToken}`  // Add your Bearer token here
                    }
                });
                
                const data = await response.json();
                
                if (data.length > 0) {
                    const subCount = data.length;  // The number of active subscriptions
                    document.getElementById('subcount').innerText = `Subcount: ${subCount}`;
                } else {
                    document.getElementById('subcount').innerText = 'No subscriptions found or unable to fetch data.';
                }
            } catch (error) {
                console.error('Error fetching subcount:', error);
                document.getElementById('subcount').innerText = 'Error fetching subcount.';
            }
        }

        // Call the function to fetch and display the subcount
        getSubcount();
    </script>
</body>
</html>
