<template lang="html">

<div v-if='film'>
  <h2>{{ film.title }}</h2>
  <h3>{{ film.director}}</h3>
  <h4>{{film.release_date}}</h4>

</div>

</template>

<script>
export default {
  name: 'film-detail',
  props: ['film']
}
</script>

<style lang="css" scoped>
</style>
