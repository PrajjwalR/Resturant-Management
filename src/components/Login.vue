<template>
  <img
    src="https://img.freepik.com/free-vector/bird-colorful-logo-gradient-vector_343694-1365.jpg"
    class="logo"
  />
  <h1>Login Page</h1>
  <div class="login">
    <input type="email" placeholder="Enter Email" v-model="email" />
    <input type="password" placeholder="Enter Password" v-model="password" />
    <button v-on:click="login" class="button">Login</button>
    <p><router-link to="/sign-up"> Sign Up </router-link></p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "LoginCompo",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async login() {
      let result = await axios.get(
        ` http://localhost:3000/users?email=${this.email}&password=${this.password}`
      );
      // console.log(result);
      if (result.status == 200 && result.data.length > 0) {
        localStorage.setItem("user-info", JSON.stringify(result.data[0]));
        this.$router.push({
          name: "Home",
        });
      }
      console.log(result);
    },
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push({
        name: "Home",
      });
    }
  },
};
</script>
