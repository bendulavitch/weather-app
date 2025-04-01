<template>
  <form v-on:submit.prevent="getWeather" class="weather-form">
    <div class="input-group">
      <label for="zipcode" class="input-label">Enter Zip Code:</label>
      <input 
        type="text" 
        id="zipcode" 
        v-model="zipcode" 
        placeholder="e.g., 90210" 
        class="input-field"
        required
      />
    </div>

    <div class="submit-button-container">
      <input 
        type="submit" 
        value="Get Weather!" 
        class="submit-button"
      />
    </div>

    <div v-if="weatherObj.name" class="weather-info">
      <p class="location">You are in {{ weatherObj.name }} and today is {{ weatherObj.date }}</p>
      <p>It is {{ weatherObj.temperature }}° and feels like {{ weatherObj.feelsLike }}°</p>
      <p>Humidity: {{ weatherObj.humidity }}%</p>
      <p>Weather: {{ weatherObj.description }}</p>
      <img :src="image" alt="Weather icon" class="weather-icon" />
    </div>
  </form>
</template>

<script>
import weatherService from '../services/WeatherService'

export default {
  data() {
    return {
      zipcode: '',
      weatherObj: {},
      image: ''
    }
  },
  methods: {
    getWeather() {
      console.log("Getting weather for zip code:", this.zipcode);
      this.weatherObj = {};

      weatherService.getWeather(this.zipcode)
        .then((response) => {
          console.log("Weather data for zip code:", this.zipcode, response.data);
          
          if (response.data) {
            this.weatherObj = response.data;
            this.image = "https://openweathermap.org/img/wn/" + this.weatherObj.icon + ".png";
          } else {
            console.error("Error: Weather data not available.");
          }
        })
        .catch((error) => {
          console.error("Error fetching weather data:", error);
        });
    }
  }
}
</script>

<style scoped>
.weather-form {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #f9f9f9;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.input-label {
  font-size: 1.2rem;
  color: #333;
  margin-bottom: 8px;
  display: block;
}

.input-field {
  width: 100%;
  padding: 12px;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 20px;
  box-sizing: border-box;
}

.submit-button {
  width: 100%;
  padding: 12px;
  font-size: 1rem;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.submit-button:hover {
  background-color: #45a049;
}

.weather-info {
  margin-top: 20px;
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #e0f7fa;
}

.location {
  font-weight: bold;
  font-size: 1.2rem;
  color: #00796b;
}

.weather-icon {
  width: 80px;
  height: 80px;
  margin-top: 10px;
  display: block;
  margin: 0 auto;
}
</style>
