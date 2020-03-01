<template lang="html">

<div v-if='film'>
  <h2><b>Favourite Film List</b></h2>
      <h3>{{ film.title }}</h3>
      <h4>{{ film.release_date }}</h4>
  </div>


</div>

</template>

<script>

export default {
  name: 'fav-film-list',
  props: ['film']
}
</script>

<style lang="css" scoped>


</style>
