<template>
  <div id="app">
    <bg></bg>
    <layer></layer>
    <headerInfo :tvShow="tvShow"></headerInfo>
    <contentInfo :episodes="episodes"></contentInfo>
    <footerInfo :tvShow="tvShow"></footerInfo>
  </div>
</template>

<script>
import 'es6-promise/auto'

import Bg from './components/Header/Background.vue'
import Layer from './components/Header/Layer.vue'
import HeaderInfo from './components/Header/Info.vue'
import ContentInfo from './components/Content/Info.vue'
import FooterInfo from './components/Footer/Info.vue'


export default {
  name: 'app',
  components: {
    Bg,
    Layer,
    HeaderInfo,
    ContentInfo,
    FooterInfo,
  },
  data: () => ({
    tvShow: '',
    episodes: []
  }),
  created: function () {
    var url1 = 'dist/SHOW123.json'
    var url2 = 'dist/EPISODES.json'
    this.getJsonData(url1, 'tvShow', this)
    this.getJsonData(url2, 'episodes', this)
  },
  methods: {
    getJsonData: (tvShow, variable, self) => {
      var xhr = new XMLHttpRequest()
      xhr.open('GET', tvShow)
      xhr.onload = function () {
        var response = JSON.parse(xhr.response)
        if (variable == 'tvShow') {
          self.tvShow = response
        } else {
          for (var i = response.length - 1; i >= 0; i--) {
            response[i] != null ? self.episodes.push({show: false, value: response[i]}) : ''
          }
        }
      }.bind(variable)
      xhr.send()
    }
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Nunito');
  body {
   margin: 0;
   padding: 0;
   font-family: 'Nunito', sans-serif;
   background-color: #474747;
  }
</style>