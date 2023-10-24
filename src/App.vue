<template>
  <main>
    <ul>
      <li v-for="user in users" :key="user.id"> ID: {{ user.id }} </li>
      <li v-for="user in users" :key="user.uid"> UID: {{ user.uid }} </li>
      <li v-for="user in users" :key="user.city"> City: {{ user.city }} </li>
      <li v-for="user in users" :key="user.street_name"> Street Name: {{ user.street_name }} </li>
      <li v-for="user in users" :key="user.street_address"> Street Address: {{ user.street_address }} </li>
    </ul>
  </main>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return { users: [] };
  },
  async mounted() {
    try {
      const response = await axios.get("https://random-data-api.com/api/address/random_address");
      this.users = [response.data];
    } catch (e) {
      console.log(e); //Error handling
    }
  }
};
</script>