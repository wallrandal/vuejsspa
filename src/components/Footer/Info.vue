<template>
  <div id="footerInfo">
    <footerTab :tvShow="tvShow"></footerTab>
  </div>
</template>

<script>

import footerTab from './Tab.vue'

export default {
  name: 'footerInfo',
  components: {
    footerTab
  },
  props: ['tvShow']
 }
</script>

<style lang="scss">
  #footerInfo {
    background-color: #474747;
    width: 100%;
    position:relative;
    min-height: 27vh;
    max-height: 37vh;
    color: #c6c6c6;
    z-index: 1;
  }
</style>
