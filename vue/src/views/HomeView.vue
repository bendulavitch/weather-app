<template>
  <div class="home">
    <h1>Welcome to the Weather App!</h1>
    <p>We are glad to have you here. You can check the weather by visiting the <router-link to="/weather">Weather Page</router-link>.</p>
  </div>
</template>

<script>
export default {
};
</script>

<style scoped>
.home {
  text-align: center;
  padding: 20px;
  margin-top: 50px;
}

h1 {
  color: #333;
  font-size: 2em;
}

p {
  font-size: 1.2em;
  color: #555;
}

router-link {
  color: #ff6f61; /* Orange color for the link */
  text-decoration: none;
  font-weight: bold;
}

router-link:hover {
  text-decoration: underline;
}
</style>
