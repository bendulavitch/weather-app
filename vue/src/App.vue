<template>
  <div id="capstone-app">
    <div id="nav">
      <router-link v-bind:to="{ name: 'home' }" class="nav-link">Home</router-link>
      <span>|</span>
      <router-link v-bind:to="{ name: 'weather' }" v-if="$store.state.token != ''" class="nav-link">Weather</router-link>
      <span>|</span>
      <router-link v-bind:to="{ name: 'logout' }" v-if="$store.state.token != ''" class="nav-link">Logout</router-link>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  name: 'App'
};
</script>

<style scoped>
#capstone-app {
  font-family: 'Arial', sans-serif;
  background-color: #f0f0f0;
}

#nav {
  display: flex;
  justify-content: center;
  background-color: #ff7e5f;
  padding: 15px 0;
  color: white;
  font-size: 1.2rem;
  font-weight: bold;
  border-bottom: 2px solid #feb47b;
}

.nav-link {
  text-decoration: none;
  color: white;
  margin: 0 10px;
  padding: 5px 10px;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.nav-link:hover {
  background-color: #feb47b;
  color: #333;
}

#nav span {
  margin: 0 5px;
}

router-view {
  padding: 20px;
}
</style>
