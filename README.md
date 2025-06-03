# weather 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: linear-gradient(to bottom, #4facfe, #00f2fe); /* Blue to Light Cyan */
            color: white;
            margin: 0;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .search-container {
            margin-bottom: 20px;
        }

        input[type="text"] {
            padding: 10px;
            font-size: 1rem;
            border: none;
            border-radius: 5px;
            margin-right: 10px;
            width: 200px;
        }

        button {
            padding: 10px;
            font-size: 1rem;
            border: none;
            background: #007bff;
            color: white;
            border-radius: 5px;
            cursor: pointer;
        }

        .weather-container {
            background: rgba(0, 0, 0, 0.3);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        h1 {
            font-size: 2rem;
            margin: 0;
        }

        h2 {
            font-size: 3rem;
            margin: 10px 0;
        }

        p, small {
            font-size: 1rem;
            margin: 5px 0;
        }

        .date {
            font-size: 1rem;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="search-container">
        <input type="text" id="cityInput" placeholder="Search for a city">
        <button onclick="updateWeather()">Search</button>
    </div>
    <div class="weather-container">
        <div class="date" id="currentDate"></div>
        <h1 id="city">Manila, Las Pinas</h1>
        <h2 id="temperature">15°C</h2>
        <p id="condition">Sunny</p>
        <small id="range">13°C / 16°C</small>
    </div>
    <script>
        // Set the current date
        const currentDateElement = document.getElementById("currentDate");
        const date = new Date();
        const options = { weekday: "long", month: "long", day: "numeric" };
        currentDateElement.innerText = date.toLocaleDateString("en-US", options);

        // Example static data (replace with an API for real weather data)
        const weatherData = {
            "Manila, Las Pinas": { temp: 15, condition: "Sunny", min: 13, max: 16 },
            "New York": { temp: -2, condition: "Snowy", min: -5, max: 0 },
            "Tokyo": { temp: 10, condition: "Cloudy", min: 8, max: 12 }
        };

        // Function to update the weather based on user input
        function updateWeather() {
            const cityInput = document.getElementById("cityInput").value.trim();
            const cityName = cityInput || "Manila, Las Pinas"; // Default to Manila if input is empty
            const data = weatherData[cityName];

            if (data) {
                document.getElementById("city").innerText = cityName;
                document.getElementById("temperature").innerText = `${data.temp}°C`;
                document.getElementById("condition").innerText = data.condition;
                document.getElementById("range").innerText =` ${data.min}°C / ${data.max}°C`;
            } else {
                alert("City not found. Try another one!");
            }
        }
    </script>
</body>
</html>
