<template>
  <Header></Header>
  <h1>Hello welcome to the Update Page</h1>
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
    <button type="button" class="buttonForUpdate" v-on:click="updateResturant">
      Update Resturant
    </button>
  </form>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";
export default {
  name: "UpdateCompo",
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
    async updateResturant() {
      const result = await axios.put(
        "http://localhost:3000/resturant/" + this.$route.params.id,
        {
          name: this.resturant.name,
          address: this.resturant.address,
          contact: this.resturant.contact,
        }
      );
      if (result.status == 200) {
        this.$router.push({ name: "Home" });
      }
    },
  },
  async mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({
        name: "SignUp",
      });
    }
    const result = await axios.get(
      "http://localhost:3000/resturant" + this.$route.params.id
    );
    // console.log(this.$route.params.id);
    this.resturant = result.data;
  },
  components: {
    Header,
  },
};
</script>

<style>
.buttonforUpdate {
  padding: 100px;
}
</style>
