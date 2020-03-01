<template>
  <div id="app">
    <div class="title">
      <h1>STUDIO GHIBLI APP</h1>
    </div>
    <div class="flex-cointainer">
      <film-list v-for="(film, index) in films" :key="index" :film="film"></film-list>
      <film-detail :film='selectedFilm'/>
      <fav-film-list :film='favFilm'/>
    </div>
  </div>
</div>
</div>
</template>

<script>
import { eventBus } from './main.js';
import FilmList from './components/FilmList.vue';
import FilmDetail from './components/FilmDetail.vue';
import FavFilmList from './components/FavFilms.vue';

export default {
  name: 'App',
  data(){
    return {
      films: [],
      selectedFilm: null,
      favFilm: null

    }
  },


  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    })
    eventBus.$on('fav-film', (film) =>{
      this.favFilm = film
    })

  },

  components: {
    'film-list': FilmList,
    'film-detail': FilmDetail,
    'fav-film-list': FavFilmList
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

.flex-container {
    justify-content: space-between;
    display: inline-flex;
}

h1 {
  font-size: 3em;
  color: black;
}

ul {
  list-style: none;
  width: 20em;
  margin-left: auto;
  margin-right: auto;
}

.title {

  color: #dda0dd;
  border-style: solid;
  border-color: black;
  text-align: center;
  width: 50%;
  margin-left: auto;
  margin-right: auto;

}

</style>
