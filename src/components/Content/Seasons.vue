<template>
  <div class="seasons">
    <div class="seasons__tabs">
    	<tabs
	      :tabs="tabs"
	      :currentTab="currentTab"
	      :wrapper-class="'seasons__tabs__default-tabs'"
	      :tab-class="'seasons__tabs__default-tabs__item'"
	      :tab-active-class="'seasons__tabs__default-tabs__item_active'"
	      :line-class="'seasons__tabs__default-tabs__active-line'"
	      @onClick="handleClick"
	    />
      <div v-if="currentTab === 'tab1'" class="seasons__tabs__content">
      	<ul v-for="episode in episodes">
      		<li v-if="episode != null && episode.value.SeasonNumber == '1'" >
      			<span class="seasons__tabs__content__title" v-on:click="episode.show = !episode.show" :id="episode.value.ID">{{episode.value.EpisodeNumber}} {{episode.value.Title}}</span>
      			<img src="dist/img/play-small-player-w.svg" alt="Reproduzir">
      			<transition name="fade">
      				<div class="seasons__tabs__content__synopsis" v-if="episode.show">
	      				<div class="seasons__tabs__content__synopsis__content">{{episode.value.Synopsis}}</div>
	      				<div class="seasons__tabs__content__synopsis__img">
	      					<img :src="episode.value.Image" :alt="episode.value.Title">
	      				</div>
	      			</div>
      			</transition>
      			<hr>
      		</li>
      	</ul>
      </div>
      <div v-if="currentTab === 'tab2'" class="seasons__tabs__content">
        <ul v-for="episode in episodes">
      		<li v-if="episode != null && episode.value.SeasonNumber == '2'" >
      			<span class="seasons__tabs__content__title" v-on:click="episode.show = !episode.show" :id="episode.value.ID">{{episode.value.EpisodeNumber}} {{episode.value.Title}}</span>
      			<img src="dist/img/play-small-player-w.svg" alt="Reproduzir">
      			<transition name="fade">
      				<div class="seasons__tabs__content__synopsis" v-if="episode.show">
	      				<div class="seasons__tabs__content__synopsis__content">{{episode.value.Synopsis}}</div>
	      				<div class="seasons__tabs__content__synopsis__img">
	      					<img :src="episode.value.Image" :alt="episode.value.Title">
	      				</div>
	      			</div>
      			</transition>
      			<hr>
      		</li>
      	</ul>
      </div>
	    </div>
    </div>
  </div>
</template>

<script>
import Tabs from 'vue-tabs-with-active-line'

export default {
  name: 'seasons',
  components: { Tabs },
  methods: {
    handleClick(newTab) {
      this.currentTab = newTab;
    }
  },
  props: ['episodes'],
  data: () => ({
    tabs: [{title: 'T1', value: 'tab1',}, {title: 'T2', value: 'tab2',}],
    currentTab: 'tab1',
    content: '',
    seasons: [],
    show: []
  }),
 }
</script>

<style lang="scss">
    ::-webkit-scrollbar {
	   width: 0px;
	   background: transparent;
	}
  .seasons {
  	position: absolute;
  	z-index: 2;
  	width: -webkit-fill-available;
  	float: right;
  	height: 70vh;
  	margin: 100px;
    overflow-x: hidden;
    overflow-y: scroll;

  	&__tabs {
	  	width: 40%;
	  	float: right;
	  	&__default-tabs {
		    position: relative;
		    max-width: 100%;
		    &__item {
		      display: inline-block;
		      margin: 0 5px;
		      // padding: 10px;
		      // padding-bottom: 8px;
		      font-size: 22px;
		      letter-spacing: 0.8px;
		      color: gray;
		      text-decoration: none;
		      border: none;
		      background-color: transparent;
		      border-bottom: 2px solid transparent;
		      cursor: pointer;
		      transition: all 0.25s;
		      &_active {
		        color: white;
		      }
		      &:hover {
		        border-bottom: 2px solid gray;
		        color: white;
		      }
		      &:focus {
		        outline: none;
		        border-bottom: 2px solid gray;
		        color: white;
		      }
		      &:first-child {
		        margin-left: 0;
		      }
		      &:last-child {
		        margin-right: 0;
		      }
		    }
		    &__active-line {
		      position: absolute;
		      bottom: 0;
		      left: 0;
		      height: 2px;
		      transition: transform 0.4s ease, width 0.4s ease;
		    }
			}
	  	&__content {
		    color: #c6c6c6;
		    font-weight: normal;
		    font-size: 20px;
		    &__title {
		    	cursor: pointer;
		    }
		    ul {
			    list-style-type: none;
		    	padding: 0;
			    li{
			    	display: block;
			    	img {
			    		margin-right: 10px; 
			    		margin-top: 2px; 
			    		width: 30px;
			    		transition: all .2s ease-in-out;
			    		float: right;
						&:hover {
							transform: scale(1.1);
						}
			    	}
					hr {
						border-color: #c6c6c6;
					}
			    } 
		    }
		    &__synopsis {
		    	display: flex;
		    	justify-content: space-between;
		    	&__content {
		    		font-size: 14px;
					width: 40%;
		    	}
		    	&__img {
		    		text-align: bottom;
		    		img {
		    			bottom: 0;
		    			min-width: 200px;
		    		}
		    	}
		    }
	  	}
  	}
  }
  .fade-enter-active, .fade-leave-active {
	  transition: opacity 0.35s ease-out;
	}

	.fade-enter, .fade-leave-to {
	  opacity: 0;
	}
</style>
