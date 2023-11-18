<!-- WeatherInput.vue -->
<template>
    <div>
      <form @submit.prevent="getWeather">
        <label for="city">Enter City:</label>
        <input v-model="city" type="text" id="city" required>
        <button type="submit" :disabled="loading">
          <span v-if="loading">Loading...</span>
          <span v-else>Get Weather</span>
        </button>
      </form>
  
      <div v-if="error" class="error-message">{{ error }}</div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        city: "Minsk",
        error: null,
        loading: false,
      };
    },
    methods: {
      async getWeather() {
        this.$emit('clearWeatherData');
        try {
          this.loading = true;
          
          const response = await this.$axios.get(
            `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=042c263f0ab874270f54d6cb02ea4fa9`
          );
  
          if (response.status === 200) {
            console.log(response.data);
            this.error = null;
            this.$emit('weatherData', response.data);
          } else {
            this.error = `Error fetching weather data: ${response.statusText}`;
          }
        } catch (error) {
          this.error = `Error fetching weather data: ${error.message}`;
        } finally {
          this.loading = false;
        }
      },
    },
  };
  </script>
  
  <style>
  .error-message {
    color: red;
    margin-top: 10px;
  }
  
  button:disabled {
    cursor: not-allowed;
    opacity: 0.5;
  }
  </style>
  