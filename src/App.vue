<template>
  <main>
    <ul>
      <li v-for="user in users" :key="user.id"> 
        {{ user.name }} <!--display results-->
      </li>
    </ul>
  </main>
</template>

<script>
  import axios from "axios";

  export default {
    data() {
      return { users: [] }  // variables
    },
    async mounted() {
      try {
        const response = await axios.get("https://jsonplaceholder.typicode.com/users"); //example api
        this.users = response.data; //update the users data 
      } catch (e) { console.log(e) } // error handling
    }
  }
</script>