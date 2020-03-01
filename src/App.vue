<template>
  <div id="app">
    <h1>STUDIO GHIBLI APP</h1>
    <div class="main cointainer">

      <!-- <form v-on:submit.prevent>
  <select v-on:change="handleSelect" v-model="selectedFilm">
    <option v-for="film in films" :film="film">{{film.title}}</option>
  </select>
</form> -->

      <ul>
        <film-list v-for="(film, index) in films" :key="index" :film="film"></film-list>
      </ul>
      <film-detail :film='selectedFilm'/>
        <div class="flex=wrapper">
          <div class="right">
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

.main-container {
  display: flex;
  justify-content: space-between;
  width: 80%;
  margin: 0 auto;
}

h1 {
  font-size: 3em;
  color: #01c1e6;
}

.list {
  width: 100%;
  display: flex;
}

.flex-wrapper {
  display: flex;
  justify-content: space-between;
}

.right {
  width: 45%;
  height: fit-content;
}

</style>
