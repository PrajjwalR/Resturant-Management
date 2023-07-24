<template>
  <Header></Header>
  <h1>Hello welcome to the Add Resturant Page</h1>
  <form class="add">
    <input
      type="text"
      placeholder="Enter Name of Resturant"
      name="name"
      v-model="resturant.name"
    />
    <input
      type="text"
      placeholder="Enter Address of Resturant"
      name="address"
      v-model="resturant.address"
    />
    <input
      type="text"
      placeholder="Enter Contact Details"
      name="contact"
      v-model="resturant.contact"
    />
    <button type="button" v-on:click="addResturant">Add Details</button>
  </form>
</template>

<script>
import axios from "axios";
import Header from "./Header.vue";
export default {
  name: "AddCompo",
  components: {
    Header,
  },
  data() {
    return {
      resturant: {
        name: "",
        address: "",
        contact: "",
      },
    };
  },
  methods: {
    async addResturant() {
      console.log(this.resturant);
      const result = await axios.post("http://localhost:3000/resturant", {
        name: this.resturant.name,
        address: this.resturant.address,
        contact: this.resturant.contact,
      });
      if (result.status == 201) {
        this.$router.push({ name: "Home" });
      }
      console.log("result", result);
    },
  },

  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({
        name: "SignUp",
      });
    }
  },
};
</script>
