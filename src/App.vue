<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div id="app">
    <WeatherInput @weatherData="setWeatherData"  @clearWeatherData="clearWeatherData"/>
    <WeatherDisplay :weather="weatherData" v-if="weatherData" />
  </div>
</template>

<script>
import WeatherInput from "./components/WeatherInput.vue";
import WeatherDisplay from "./components/WeatherDisplay.vue";

export default {
  components: {
    WeatherInput,
    WeatherDisplay,
  },
  data() {
    return {
      weatherData: null,
    };
  },
  methods: {
    setWeatherData(data) {
      this.weatherData = data;
    },
    clearWeatherData() {
      this.weatherData = null;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
