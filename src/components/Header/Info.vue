<template>
  <div id="headerInfo" >
  	<div class="header">
  		<div class="header__title">{{tvShow.Title}}</div>
  		<div class="header__subtitle">
          <span v-for="item in tvShow.Genres">
            {{ item.Title | uppercase}} /
          </span> 
          {{tvShow.Year}}
      </div>
  	</div>
  	<div class="close">
  		<div class="close__icon">
  			<img src="dist/img/close-search-w.svg" alt="Fechar">
  		</div>
  	</div>
  </div>
</template>

<script>

export default {
  name: 'headerInfo',
  props: ['tvShow'],
  filters: {
    uppercase: function(value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style lang="scss">
	#headerInfo {
		position: absolute;
    width: -webkit-fill-available;
		display: flex;
		justify-content: space-between;
		//padding: 40px;
    z-index: 2;
		.header {
			margin: 40px;
			&__title {
				color: white;
				font-size: 3vw;
				font-weight: bold;
			}
			&__subtitle {
				font-weight: bold;
				color: #c6c6c6;
				font-size: 1.2vw;
			}
		}
    .close {
      margin: 40px;
      img { 
        transition: all .2s ease-in-out;
        &:hover {
          transform: scale(1.1);
        }
      }
    }
	}
</style>
