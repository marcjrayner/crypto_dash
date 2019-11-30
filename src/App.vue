<template>
  <div id="app">
    <all-coins :coinTickers="coinTickers"></all-coins>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import AllCoins from './components/AllCoins.vue'
export default {
  name: 'app',

  data() {
    return {
      coinTickers: []
    }
  },
  mounted() {
    fetch('https://api.coinlore.com/api/tickers/')
    .then(response => response.json())
    .then(coinTickersJson => this.coinTickers = coinTickersJson.data)
  },
  components: {
    'all-coins': AllCoins
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
