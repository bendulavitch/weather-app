<template>
  <div id="logout">
    <div class="logout-container">
      <h1>Goodbye!</h1>
      <p>You have been logged out successfully. See you again soon!</p>
    </div>
  </div>
</template>

<script>
export default {
  created() {
    this.$store.commit("LOGOUT");
    this.$router.push("/login");
  }
};
</script>

<style scoped>
#logout {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(135deg, #ff7e5f, #feb47b);
  font-family: 'Arial', sans-serif;
  color: white;
}

.logout-container {
  background-color: rgba(255, 255, 255, 0.1);
  padding: 40px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
  max-width: 400px;
  width: 100%;
  text-align: center;
}

h1 {
  font-size: 3rem;
  font-weight: 700;
  margin-bottom: 20px;
}

p {
  font-size: 1.2rem;
  margin-bottom: 20px;
}

.logout-container a {
  color: #6e7dff;
  font-size: 1rem;
  text-decoration: none;
}

.logout-container a:hover {
  text-decoration: underline;
}
</style>
