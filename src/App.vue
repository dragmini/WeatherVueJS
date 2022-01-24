<template>
  <div id="app">
    <Header  @search-weather="searchWeather" @open-options-modal="openOptionsModal"></Header>
    <transition name="fade">
      <Options v-if="this.activeOptionsModal"></Options>
    </transition>
    <CardsCity :searchText="this.searchText"></CardsCity>
  </div>
</template>

<script>
import Header from './components/HeaderMenu.vue';
import CardsCity from './components/CardsCity.vue';
import Options from './components/Options.vue'


export default {
  name: 'App',
  // props: {
    // searchText: {type: String},
    // activeOptionsModal: {type: Boolean}
  // },
  data() {
    return {
      activeOptionsModal: false,
      searchText: ''
    }
  },
  components: {
    Header,
    CardsCity,
    Options
  },
  methods: {
    searchWeather(data) {
      this.searchText = data.searchText
      // console.log(this.searchText)
    },
    openOptionsModal() {
      this.activeOptionsModal = !this.activeOptionsModal
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
  height: 100%;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .65s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}
</style>
