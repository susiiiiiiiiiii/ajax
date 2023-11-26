document.getElementById('location-form').addEventListener('submit', function(event) {
    event.preventDefault();
    let location = document.getElementById('location-input').value;
    getWeather(location);
});

async function getWeather(location) {
    // Replace 'YOUR_API_KEY' with your actual API key
    let apiKey = '93fa968e0c412b9f33a66e1833fc3337';
    
    try {
        let response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${location}&appid=${apiKey}&units=metric`);
        let data = await response.json();

        if (data.cod === '404') {
            alert('Location not found.');
        } else {
            document.getElementById('location-name').innerText = data.name;
            document.getElementById('weather-description').innerText = data.weather[0].description;
            document.getElementById('temperature').innerText = Math.round(data.main.temp) + '°C';
            document.getElementById('weather-display').classList.remove('hidden');
        }
    } catch (error) {
        console.error('Error fetching weather data:', error);
        alert('An error occurred while fetching weather data.');
    }
}
