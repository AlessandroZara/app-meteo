<template>
  <WeatherApp></WeatherApp>
</template>

<script>

import WeatherApp from './views/Weather.vue'
export default {
components:{
    WeatherApp,
}
}
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
