<template>
  <div id="app">
    <h2>Vue WebAPI</h2>
    <CoinGecko></CoinGecko>
    <p>Data source <a href="https://api.coingecko.com/api/v3/coins/markets"><code>https://api.coingecko.com/api/v3/coins/markets</code></a></p>

    <AnimeList></AnimeList>
    <p>Data source <a href="https://anime-facts-rest-api.herokuapp.com/api/v1"><code>https://anime-facts-rest-api.herokuapp.com/api/v1</code></a></p>

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

