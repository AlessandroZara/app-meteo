<template>
  <div id="weatherApp">
    <form v-on:submit.prevent="getWeather">
      <p><input type="text" name="location" v-model="location" /></p>
      <p><button class="btn btn-primary">Search</button></p>
    </form>
    <div v-if="displayWeather" class="container display-weather-section">
      <h1>{{ weatherList.name }}</h1>
      <h2>{{ weatherList.sys.country }}</h2>
      <img v-bind:src="'http://openweathermap.org/img/w/' + weatherList.weather[0].icon + '.png' "  />
      <coord v-bind:coord="weatherList.coord"></coord>
      <weather-display
        v-bind:weatherDisplay="weatherList.weather[0].main"
      ></weather-display>
      <temperature v-bind:temperature="weatherList.main"></temperature>
      <winds v-bind:wind="weatherList.wind"></winds>
      <clouds v-bind:cloud="weatherList.clouds"></clouds>
      <sun v-bind:sun="weatherList.sys"></sun>
    </div>
  </div>
</template>

<script>
import Coord from "../components/coord.vue";
import Clouds from "../components/cloud.vue";
import Sun from "../components/sun.vue";
import Temperature from "../components/temperature.vue";
import Winds from "../components/wind.vue";
import WeatherDisplay from "../components/vueDsiplay.vue";
export default {
  components: {
    Coord,
    Clouds,
    Sun,
    Temperature,
    Winds,
    WeatherDisplay,
  },
  data() {
    return {
      location: "",
      apiKey: process.env.VUE_APP_WEATHER_API_KEY,
      weatherList: undefined,
      displayWeather: false,
    };
  },
  methods: {
    getWeather() {
      function getGithubOrgs(url) {
        return fetch(url).then((response) => response.json());
      }

      getGithubOrgs(`http://api.openweathermap.org/data/2.5/weather?q=${this.location}&appid=${this.apiKey}`).then(
        (res) => {console.log(res)
        this.weatherList=res 
        this.displayWeather=true;
         } );
    },
  },
};
</script>

<style></style>

