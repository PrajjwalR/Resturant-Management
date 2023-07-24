<template>
  <Header></Header>
  <h1>Hello {{ name }}, Welcome to the Home Page</h1>
  <table class="table" border="1">
    <tr>
      <td>Id</td>
      <td>Name</td>
      <td>Add.</td>
      <td>Contact</td>
      <td>Actions</td>
    </tr>
    <tr v-for="item in resturants" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.address }}</td>
      <td>{{ item.contact }}</td>
      <td>
        <router-link :to="'/update/' + item.id">Update</router-link>
        <button v-on:ckick="deleteResturant(item.id)">Delete</button>
      </td>
    </tr>
  </table>
</template>

<script>
import axios from "axios";
import Header from "./Header.vue";
export default {
  name: "HomeCompo",
  data() {
    return {
      name: "",
      resturants: [],
    };
  },
  methods: {
    async deleteResturant(id) {
      let result = await axios.delete("http://localhost:3000/resturant/" + id);
      if (result.status == 200) {
        this.loadData();
      }
    },
    async loadData() {
      let user = localStorage.getItem("user-info");
      this.name = JSON.parse(user).name;
      if (!user) {
        this.$router.push({
          name: "SignUp",
        });
      }
      let result = await axios.get("http://localhost:3000/resturant");
      console.log(result);
      this.resturants = await result.data;
    },
  },
  mounted() {
    this.loadData();
  },
  components: {
    Header,
  },
};
</script>

<style>
.table {
  margin: auto;
}
td {
  width: 150px;
  height: 50px;
}
</style>
