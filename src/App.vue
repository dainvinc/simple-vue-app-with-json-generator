<template>
  <div id="app">
    <div>
      <img alt="Vue logo" src="./assets/logo.png">
      <div class="p-1r" v-if="!profiles.length">
        Here's some random data generated using json-generator.com
        Click on the below button to get started...
      </div>
    </div>
    <button @click="getRandomData" v-if="!profiles.length">Load profiles</button>
    <div v-if="isLoading">Loading...</div>
    <div v-for="profile in profiles" :key="profile.id">
      <Card :email="profile.email" :personalDetails="profile.profile" />
    </div>
  </div>
</template>

<script>
import Card from './components/Card.vue'
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      isLoading: false,
      profiles: [],
    };
  },
  components: {
    Card
  },
  methods: {
    getRandomData() {
      this.isLoading = true;

      axios
        .get('https://api.json-generator.com/templates/tfe-NATUyD71/data?access_token=1jimxiblxnop07n9r0red3toqgguhrke60ldjyfe')
        .then(({ data }) => {
          console.log(data);
          this.profiles = data;
          this.isLoading = false;
        });
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.p-5 {
  padding: 5px;
}

.p-1r {
  padding: 1rem;
}

button {
  border: 0;
  border-radius: 5px;
  padding: 12px;
  background-color: lightgreen;
  font-weight: 600;
}

button:hover {
  background-color: rgb(85, 255, 0);
  cursor: pointer;
}
</style>
