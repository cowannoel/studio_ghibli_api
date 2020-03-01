<template lang="html">

<div v-if='film'>
  <h2>{{ film.title }}</h2>
    <h3>{{ film.director}}</h3>
      <h4>{{film.release_date}}</h4>
      <button type="button" name="favorite" v-on:click="handleFavClick">Add to Favourite Films</button>
</div>

</template>

<script>

import { eventBus } from '../main.js'

export default {
  name: 'film-detail',
  props: ['film'],
  methods: {
    handleFavClick(){
      console.log('film', this.film);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
