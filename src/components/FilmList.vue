<template lang="html">
<div class="">
    <li @click="handleClick">{{ film.title }}</li>
  </select>
</div>

</template>

<script>

import { eventBus } from '../main.js'

export default {
  name: 'film-list',
  props: ['film'],
  methods: {
    handleClick(){
      eventBus.$emit('film-selected', this.film)
    }
  }
}
</script>

<style lang="css" scoped>
li {
  list-style: none;
}
</style>
