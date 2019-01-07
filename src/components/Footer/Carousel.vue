<template>
  <div id="FooterCarousel">
  	<carousel ref="item" class="FooterCarousel" :dots="true" :nav="false" :items="3" :rewind="true" :stagePadding="5">
			<div  class="FooterCarousel__item">
				<div class="FooterCarousel__item__actor">{{cast[0].Name}}</div>
				<div class="FooterCarousel__item__character">Mark Doe</div>
			</div>
			<div  class="FooterCarousel__item">
				<div class="FooterCarousel__item__actor">{{cast[1].Name}}</div>
				<div class="FooterCarousel__item__character">Mark Doe</div>
			</div>
			<div  class="FooterCarousel__item">
				<div class="FooterCarousel__item__actor">{{cast[2].Name}}</div>
				<div class="FooterCarousel__item__character">Mark Doe</div>
			</div>
	</carousel>
  </div>
</template>

<script>
import carousel from 'vue-owl-carousel'

export default {
 	name: 'FooterCarousel',
 	components: { carousel },
 	props: ['dots', 'items', 'rewind', 'stagePadding', 'nav', 'cast'],
}

</script>

<style lang="scss">
  #FooterCarousel {
	font-size: 16px;
	.FooterCarousel__item {
		background-color: #212121;
		text-align: center;
		margin-top: 40px;
		padding: 30px;
		&__actor {
			font-weight: bold;
		}
	}
  }
</style>
