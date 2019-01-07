<template>
  <div id="layer"></div>
</template>

<script>


export default {
  name: 'layer',
 }
</script>

<style lang="scss">
  #layer {
    position: absolute;
    height: 90vh;
    min-width: -webkit-fill-available;
    background-image: -webkit-linear-gradient(black, transparent, transparent);
    background-image: -o-linear-gradient(black, transparent, transparent);
    background-image: linear-gradient(black, transparent, transparent);
    opacity: .8;
    z-index: 1;
    &__body {
      position: relative;
      height: 90vh;
    }
  }
</style>
