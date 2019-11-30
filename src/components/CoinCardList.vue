<template lang="html">
<div >
  <ul>
    <coin-card v-for="(ticker, index) in coinTickers" :ticker="ticker" :key="index" v-if="ticker && ticker.rank < 10"></coin-card>
  </ul>
</div>

</template>

<script>
import CoinCard from './CoinCard.vue'

export default {
  name: 'coin-card-list',
  props: ['coinTickers'],
  components: {
    'coin-card': CoinCard
  }
}


</script>

<style lang="css" scoped>

ul {
  list-style-type: none;
  display: flex;
  flex-wrap: wrap;
  align-items: stretch;
}

</style>
