<template>
  <div id="contentInfo">
    <seasons :tabs="tabs" :episodes="episodes"></seasons>
  </div>
</template>

<script>
import Seasons from './Seasons.vue'

export default {
  name: 'contentInfo',
  props: ['episodes', 'tabs'],
  components: {Seasons},
 }
</script>

<style lang="scss">
  #contentInfo {
  	position: relative;
  	height: 90vh;
  	background-image: linear-gradient(90deg, transparent, black);
    min-width: -webkit-fill-available;
  }
</style>
