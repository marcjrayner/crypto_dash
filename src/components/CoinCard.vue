<template lang="html">
  <div v-on:click="handleClick" class="card">
    <div class="logo">
      <img class="coin":src="logoURL" alt="">
      <h4>{{ticker.name}}</h4>
      <h2>{{ticker.percent_change_7d}}%</h2>
    </div>
    <hr>
    <ul>
      <li>{{ticker.symbol}}: 1.00</li>
      <li>BTC: {{ticker.price_btc}}</li>
      <li>USD: {{ticker.price_usd}}</li>
      <li>Vol: {{ticker.volume24a}}</li>
      <coin-detail :coin="selectedCoin"></coin-detail>
    </ul>


  </div>


</template>

<script>
import CoinDetail from './CoinDetail.vue'
import {eventBus} from '../main.js'
export default {
  name: 'coin-card',
  data() {
    return {
      logoURL: 'https://raw.githubusercontent.com/rainner/binance-watch/master/public/images/icons/' + this.ticker.symbol.toLowerCase() + '_.png',
      selectedCoin: this.ticker
    }
  },
  props: ['ticker'],
  methods: {
    handleClick() {
      eventBus.$emit('coin-selected', this.ticker)
    }
  },
  components: {
    'coin-detail': CoinDetail
  }
}
</script>

<style lang="css" scoped>
h4 {
  /* display: flex;
  align-self: center; */
  text-align: center;
  text-align-last: center;
}
h2 {
  text-align: right;
}
ul {
  list-style-type: none;
  padding: 0px, 0px, 0px, 0px;
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  justify-content: space-between ;
}
li {
  font-size: 0.7em;
  display: flex;
  align-content: flex-start;
  justify-content: flex-start;
}
.percentage {
  text-align: right;
}
.logo {
  display: flex;
  justify-content: space-around;
}
.card {
  background: #eee;
  padding: 10px 10px;
  margin: 10px 10px;
  width: 28%;
  /* display: flex; */
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}
.coin {
height: 4em;
width: 4em;
}
</style>
