<template>
  <router-view></router-view>
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.logo {
  width: 150px;
  height: 150px;
  border-radius: 20px;
}
.register input,
.login input,
.add input {
  width: 200px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
  border: 1px solid rgb(0, 143, 143);
  border-radius: 10px;
}
.button,
.add button {
  width: 130px;
  height: 30px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
  border: 1px solid black;
  border-radius: 10px;
  text-align: center;
  background-color: rgb(225, 192, 255);
}
</style>
