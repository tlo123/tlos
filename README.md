<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Twitch Subcount for xtlos</title>
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
        const twitchUser = 'xtlos';

        async function getSubcount() {
            try {
                // Replace this URL with the actual Twitch API endpoint for subscriptions
                // You'll need to handle OAuth authentication, and this endpoint might not exist without a subscription.
                const response = await fetch(`https://api.twitch.tv/helix/subscriptions?broadcaster_id=${twitchUser}`, {
                    method: 'GET',
                    headers: {
                        'Client-ID': 'YOUR_TWITCH_CLIENT_ID',  // Replace with your Twitch client ID
                        'Authorization': 'Bearer YOUR_ACCESS_TOKEN'  // Replace with your OAuth access token
                    }
                });
                const data = await response.json();
                if (data.data && data.data.length > 0) {
                    const subCount = data.data.length;  // You may need to modify this depending on response structure
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

