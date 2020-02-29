<template>
  <div id="app">
    <h1>STUDIO GHIBLI APP</h1>
    <div class="main cointainer">
      <ul>
        <film-list v-for="(film, index) in films" :key="index" :film="film"></film-list>
      </ul>
      <film-detail/>
    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js';
import FilmList from './components/FilmList.vue';
import FilmDetail from './components/FilmDetail';

export default {
  name: 'App',
  data(){
    return {
      films: [],
      selectedFilm: null
    }
  },


  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    })

  },

  components: {
    'film-list': FilmList,
    'film-detail': FilmDetail
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
