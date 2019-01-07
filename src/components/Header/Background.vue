<template>
  <div id="background" v-bind:style="{ 'background-image': 'url(' + image + ')' }"></div>
</template>

<script>
export default {
  name: 'background',
  data () {
    return {
      image : ''
    }
  },
  created: function () {
    var tvShow = 'https://sample-api-78c77.firebaseio.com/tv-shows/SHOW123.json'
    var xhr = new XMLHttpRequest()
    var self = this
    xhr.open('GET', tvShow)
    xhr.onload = function () {
      var response = JSON.parse(xhr.response)
      self.image = response.Images.Background
    }
    xhr.send()
  },
}
</script>

<style lang="scss">
  #background {
    height: 90vh;
    min-width: -webkit-fill-available;
    position: absolute;
    z-index: -1;
  }
</style>
