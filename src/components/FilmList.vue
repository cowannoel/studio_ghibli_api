<template lang="html">
<li>{{ film.title }}</li>
</template>

<script>
export default {
  name: 'film-list',
  props: ['film']
}
</script>

<style lang="css" scoped>
li {
  list-style: none;
}
</style>
