# prodigy-5
html
<!DOCTYPE html>
<html>
  <head>
    <title>Weather App</title>
  </head>
  <body>
    <h1>Weather App</h1>
    <input type="text" id="location-input" placeholder="Enter a location" />
    <body {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 20px;
}

#location-input {
  padding: 10px;
  font-size: 16px;
  width: 50%;
  margin-bottom: 20px;
}

#get-weather-btn {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  cursor: pointer;
}

#weather-data {
  margin-top: 50px;
} id="get-weather-btn">Get Weather</button>
    <div id="weather-data"></div>
    <script src="app.js"></script>
  </body>
</html>

css
body {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 20px;
}

#location-input {
  padding: 10px;
  font-size: 16px;
  width: 50%;
  margin-bottom: 20px;
}

#get-weather-btn {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  cursor: pointer;
}

#weather-data {
  margin-top: 50px;
}
java script
const apiKey = 'your-api-key';
const form = document.getElementById('location-form');
const locationInput = document.getElementById('location-input');
const weatherDataDiv = document.getElementById('weather-data');

form.addEventListener('submit', (e) => {
  e.preventDefault();
  const location = locationInput.value;
  getWeatherData(location);
});

function getWeatherData(location) {
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${location}&appid=${apiKey}&units=metric`;
  fetch(url)
    .then((response) => response.json())
    .then((data) => {
      displayWeatherData(data);
    })
    .catch((error) => {
      console.error(error);
      weatherDataDiv.innerHTML = 'Error fetching weather data';
    });
}

function displayWeatherData(data) {
  const { name, main, weather } = data;
  const html = `
    <h2>${name}</h2>
    <p>Temperature: ${main.temp}°C</p>
    <p>Feels like: ${main.feels_like}°C</p>
    <p>Humidity: ${main.humidity}%</p>
    <p>Weather: ${weather[0].description}</p>
  `;
  weatherDataDiv.innerHTML = html;
}
