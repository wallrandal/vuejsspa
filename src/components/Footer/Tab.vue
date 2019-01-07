<template>
  <div class="footer">
    <div class="footer__logo">
      <img src="dist/img/logo-telecine.svg" alt="Telecine">
    </div>
    <tabs
      :tabs="tabs"
      :currentTab="currentTab"
      :wrapper-class="'footer__default-tabs'"
      :tab-class="'footer__default-tabs__item'"
      :tab-active-class="'footer__default-tabs__item_active'"
      :line-class="'footer__default-tabs__active-line'"
      @onClick="handleClick"
    />
    <div class="footer__content">
      <div v-if="currentTab === 'tabA'" class="footer__content__tab">
        <div class="footer__content__tab__icons">
          <div class="footer__content__tab__icons__icon">
            <img src="dist/img/add-gray-s.svg" alt="Minha Lista"> <br> Minha Lista
          </div>
          <div class="footer__content__tab__icons__icon">
            <img src="dist/img/sad-gray-w.svg" alt="Avaliar"> <br> Avaliar
          </div>
          <div class="footer__content__tab__icons__icon">
            <img src="dist/img/rec-gray-s.svg" alt="Gravar"> <br> Gravar
          </div>
          <div class="footer__content__tab__icons__icon">
            <img src="dist/img/share-gray-s.svg" alt="Compartilhar"> <br> Compartilhar
          </div>
        </div>
        <div class="footer__content__tab__synopsis">
          {{tvShow.Synopsis}}
        </div>
      </div>
      <div v-if="currentTab === 'tabB'" class="">
        <footerCarousel :cast="tvShow.Cast"></footerCarousel>
      </div>
      <div v-if="currentTab === 'tabC'" class="footer__content__tab">
        Não há informações no momento.
      </div>
    </div>
  </div>
</template>

<script>
import Tabs from 'vue-tabs-with-active-line'
import FooterCarousel from './Carousel.vue'

const TABS = [{title: 'GERAL',value: 'tabA',}, {title: 'ELENCO',value: 'tabB',}, {title: 'PRINCIPAIS PRÊMIOS',value: 'tabC',}];

export default {
  components: {
    Tabs,
    FooterCarousel
  },
  data: () => ({
    tabs: TABS,
    currentTab: 'tabA',
  }),
  props: ['tvShow'],
  methods: {
    handleClick(newTab) {
      this.currentTab = newTab;
    },
  },
}
</script>

<style lang="scss">

.footer {
  position: relative;

  margin: 40px;
  &__logo {
    margin-top: -10px;
    position: absolute;
    min-width: -webkit-fill-available;
    margin-right: 140px;
    cursor: pointer;
    img {
      float: right;
    }
  }

  &__default-tabs {
    position: relative;
    margin: 0 auto;
    max-width: 100%;
    margin-right: 80px;
    &__item {
      display: inline-block;
      margin: 0 5px;
      font-size: 16px;
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
      background-color: green;
      transition: transform 0.4s ease, width 0.4s ease;
    }
  }

  &__content {
    &__tab {
      max-width: 100%;
      margin-top: 40px;
      font-size: 20px;
      display: flex;
      justify-content: space-between;
      &__icons {
        display: flex;
        justify-content: space-between;
        font-size: 12px;
        width: 40%;
        margin-right: 40px;
        &__icon {
          text-align: center;
          width: 100px;
          img {
            cursor: pointer;
            margin: auto;
            top: 0;
            transition: all .2s ease-in-out;
            &:hover {
              transform: scale(1.1);
            }
          }
        }
      }
      &__synopsis {
        font-size: 16px;
      }
    }
  }
}
</style>
