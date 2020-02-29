<template>
  <div id="app">
    <h1>STUDIO GHIBLI APP</h1>
    <ul>
      <film-list v-for="(film, index) in films" :key="index" :film="film"></film-list>
    </ul>

  </div>
</template>

<script>
import FilmList from './components/FilmList.vue';

export default {
  name: 'App',
  data(){
    return {
      films: []
    }
  },


  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)
  },

  components: {
    'film-list': FilmList
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
</style>
