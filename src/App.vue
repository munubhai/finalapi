<template>
  <div id="app">
    <h2>Vue WebAPI</h2>
    <CoinGecko></CoinGecko>
    <AnimeList></AnimeList>
    <!--<img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
//import HelloWorld from './components/HelloWorld.vue';
import CoinGecko from './components/CoinGecko.vue'
import AnimeList from './components/AnimeList.vue'


@Component({
  components: {
    CoinGecko,AnimeList
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body{
  background-color: lightgray ;
}

</style>

