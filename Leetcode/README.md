<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Streak Stats</title>
    <style>
        /* Add your CSS styles here */
    </style>
</head>
<body>
    <h1>Welcome, Kartikey Gupta!</h1>
    <div id="streakStatsContainer">
        <!-- Streak stats will be dynamically inserted here -->
    </div>

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
