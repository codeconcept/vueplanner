<template>
  <div id="app">
    <h3>{{ greetings }}</h3>
    <div>
      <technos v-bind:technos="technos"></technos>
    </div>   
  </div>
</template>

<script>
import TechnoList from './components/TechnoList.vue';

export default {
  name: "app",
  data() {
    return {
      greetings: "Bienvenue sur Planner",
      technos: []
    };
  },
  components: {
    technos: TechnoList
  },
  created: function() {
    // if no server, put a json file in assets and point to this.axios.get('./builds/technos.json)
    // and import it in main.js: import './assets/technos.json'
    this.axios
      .get("https://nodetestapi-legbatbehu.now.sh/technos")
      .then(response => {
        this.technos = response.data;
      });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
