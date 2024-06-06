<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kartikey Gupta's GitHub Streak Stats</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            height: 100vh;
        }

        h1 {
            color: #333;
            margin-bottom: 20px;
        }

        #streakStatsContainer {
            border: 2px solid #ddd;
            border-radius: 5px;
            overflow: hidden;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }

        #streakStatsContainer img {
            width: 100%;
            display: block;
        }

        p {
            color: #666;
        }

        a {
            color: #007bff;
            text-decoration: none;
        }

        a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <h1>Welcome, Kartikey Gupta!</h1>
    <div id="streakStatsContainer">
        <!-- Streak stats will be dynamically inserted here -->
    </div>
    <p>Check out my <a href="https://leetcode.com/KartikeyGupta" target="_blank">LeetCode profile</a> for more coding adventures!</p>

    <script>
        // Function to fetch GitHub streak stats
        async function fetchGitHubStreakStats(username) {
            const response = await fetch(`https://streak-stats.demolab.com/?user=${username}`);
            const data = await response.json();
            return data;
        }

        // Function to display streak stats on the webpage
        async function displayStreakStats() {
            const username = "KartikeyGupta"; // Your GitHub username
            const streakStatsContainer = document.getElementById("streakStatsContainer");

            try {
                const streakStats = await fetchGitHubStreakStats(username);
                // Create HTML elements to display streak stats
                const streakStatsElement = document.createElement("img");
                streakStatsElement.src = streakStats.url; // Assuming the API returns a URL to the streak stats image
                streakStatsElement.alt = "GitHub Streak Stats";

                // Append streak stats element to container
                streakStatsContainer.appendChild(streakStatsElement);
            } catch (error) {
                console.error("Error fetching streak stats:", error);
                streakStatsContainer.textContent = "Error fetching streak stats.";
            }
        }

        // Call the function to display streak stats when the page loads
        window.onload = displayStreakStats;
    </script>
</body>
</html>
