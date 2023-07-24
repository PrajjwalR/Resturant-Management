<template>
  <div class="nav">
    <router-link to="/">Home Page</router-link>
    <router-link to="add">Add Resturant</router-link>

    <a v-on:click="logout" href="#">Logout</a>
  </div>
</template>

<script>
export default {
  name: "HeaderCompo",
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style>
.nav {
  background-color: rgb(59, 59, 59);
  overflow: hidden;
  width: 100%;
}
.nav a {
  float: left;
  color: #f2f2f2;
  text-align: center;
  padding: 10px 14px;
  text-decoration: none;
  font-size: 18px;
  margin-right: 10px;
}
.nav a:hover {
  background-color: #ddd;
  color: #222;
}
</style>
