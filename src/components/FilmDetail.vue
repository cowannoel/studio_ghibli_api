<template lang="html">

<div v-if='film'>
  <h2>{{ film.title }}</h2>
    <h3>{{ film.director}}</h3>
      <h4>{{film.release_date}}</h4>
      <button v-on:click="handleFavClick" type="button" name="favourites">Add to Favourites</button>
</div>

</template>

<script>

import { eventBus } from '../main.js'

export default {
  name: 'film-detail',
  props: ['film'],
  methods: {
    handleFavClick(){
      eventBus.$emit('fav-film', this.film);
    }
    }
  }

</script>

<style lang="css" scoped>
</style>
