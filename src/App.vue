<template>
    <MainPage @changeCurrentPage="changeCurrentPage" v-if="currentPage == 'MainPage'"></MainPage>
    <WeapontypePage :weaponType="weaponType" v-if="currentPage == 'WeapontypePage'"></WeapontypePage>
</template>

<script>
import MainPage from './components/MainPage.vue';
import WeapontypePage from './components/WeapontypePage.vue';

import './assets/splatoonCss.css'

export default {
  name: 'App',
  data(){
      return {
        currentPage : 'MainPage',
        weaponType : ''
      }
    },
  components: {
    MainPage,
    WeapontypePage,
  },
  methods : {
    changeCurrentPage : function(e){
      this.currentPage = 'WeapontypePage'
      this.weaponType = e;
    },
  }
}
</script>

<style>
#app {
  text-align: center;
}
</style>
