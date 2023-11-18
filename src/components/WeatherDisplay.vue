<template>
    <div id="weatherDate">
      <h2>Weather in {{ weather.name }}, {{ weather.sys.country }}</h2>
      <p>Temperature: {{ convertKelvinToCelsius(weather.main.temp) }}°C</p>
      <p>Weather: {{ weather.weather[0].description }}</p>
    </div>
</template>
  
<script>
  export default {
    props: {
      weather: Object,
    },
    methods: {
      convertKelvinToCelsius(kelvin) {
        return (kelvin - 273.15).toFixed(0); 
      },
    },
  };
</script>
<style>
#weatherDate{
    border: 1px skyblue dotted;
}
</style>