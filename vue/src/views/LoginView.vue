<template>
  <div id="login">
    <div class="form-container">
      <h1>Please Sign In</h1>
      <div role="alert" v-if="invalidCredentials" class="alert">
        Invalid username or password!
      </div>
      <div role="alert" v-if="this.$route.query.registration" class="alert">
        Thank you for registering, please sign in.
      </div>

      <form v-on:submit.prevent="login">
        <div class="form-input-group">
          <label for="username">Username</label>
          <input type="text" id="username" v-model="user.username" required autofocus />
        </div>

        <div class="form-input-group">
          <label for="password">Password</label>
          <input type="password" id="password" v-model="user.password" required />
        </div>

        <button type="submit">Sign in</button>

        <p class="signup-link">
          <router-link v-bind:to="{ name: 'register' }">Need an account? Sign up.</router-link>
        </p>
      </form>
    </div>
  </div>
</template>

<script>
import authService from "../services/AuthService";

export default {
  components: {},
  data() {
    return {
      user: {
        username: "",
        password: ""
      },
      invalidCredentials: false
    };
  },
  methods: {
    login() {
      authService
        .login(this.user)
        .then(response => {
          if (response.status == 200) {
            this.$store.commit("SET_AUTH_TOKEN", response.data.token);
            this.$store.commit("SET_USER", response.data.user);
            this.$router.push("/");
          }
        })
        .catch(error => {
          const response = error.response;
          if (response.status === 401) {
            this.invalidCredentials = true;
          }
        });
    }
  }
};
</script>

<style scoped>
#login {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(135deg, #6e7dff, #283c86);
  font-family: 'Arial', sans-serif;
  color: white;
}

.form-container {
  background-color: rgba(255, 255, 255, 0.1);
  padding: 40px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
  max-width: 400px;
  width: 100%;
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
  font-weight: 700;
}

.form-input-group {
  margin-bottom: 1.5rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  font-size: 1rem;
}

input[type="text"],
input[type="password"] {
  width: 100%;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  font-size: 1rem;
  margin-bottom: 0.5rem;
}

button {
  background-color: #6e7dff;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  cursor: pointer;
  width: 100%;
}

button:hover {
  background-color: #283c86;
}

.alert {
  background-color: #f44336;
  color: white;
  padding: 10px;
  margin-bottom: 1.5rem;
  border-radius: 5px;
}

.signup-link {
  font-size: 1rem;
}

.signup-link a {
  color: #6e7dff;
  text-decoration: none;
}

.signup-link a:hover {
  text-decoration: underline;
}
</style>
