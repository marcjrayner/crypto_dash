<template>
  <div id="app">

  </div>
</template>

<script>
import {eventBus} from './main.js'
import AllCoins from './components/AllCoins.vue'
export default {
  name: 'app',

  data() {
    return {
      allCoins: []
    }
  },
  mounted() {
    fetch('https://api.coinlore.com/api/tickers/')
    .then(response => response.json())
    .then(coinTickers => this.allCoins = coinTickers)
  }

}


</script>

<style>

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
