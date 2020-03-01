<template lang="html">
<ul class="film-list-flex">
    <li @click="handleClick">{{ film.title }}</li>
  </select>
</ul>

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

.film-list-flex {
  flex: 1;
  padding-left: 0px;
}

</style>
