<template>
    <div class="weather-view-container">
      <weather-component />
    </div>
  </template>
  
  <script>
  import WeatherComponent from '../components/WeatherComponent.vue'
  
  export default {
    components: { WeatherComponent }
  }
  </script>
  
  <style scoped>
  .weather-view-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    padding: 20px;
    background-color: #f5f5f5;
  }
  </style>
  