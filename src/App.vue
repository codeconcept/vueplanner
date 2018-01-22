<template>
  <div id="app">
    <h3>{{ greetings }}</h3>
    <div>
      <ul>
        <li v-for="techno in technos" v-bind:key="techno._id">{{techno.name}}</li>
      </ul>
    </div>   
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      greetings: "Bienvenue sur Planner",
      technos: [
        {
          _id: "1",
          name: "Vuex",
          details: "Ecrire un comparatif Vuex vs Redux",
          dateStudy: "2018-01-29T10:00:00.397Z",
          dateCreation: "2018-01-21T17:00:46.397Z",
          timeSpentStudying: "0"
        },
        {
          _id: "2",
          name: "Angular 6",
          details: "sortie prévue le 28 mars 2018. Voir les nouveautés",
          dateStudy: "2018-04-01T10:00:00.397Z",
          dateCreation: "2018-01-21T18:42:46.007Z",
          timeSpentStudying: "0"
        },
        {
          _id: "3",
          name: "Firebase",
          details: "Jouer avec Firestore",
          dateStudy: "2018-04-01T14:00:00.007Z",
          dateCreation: "2018-01-21T18:44:46.210Z",
          timeSpentStudying: "45"
        }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
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
