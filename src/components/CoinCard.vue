<template lang="html">
<div >
  <ul>
    <li v-for="(ticker, index) in coinTickers" :ticker="ticker" :key="index" v-if="ticker && ticker.rank < 10">{{ticker.name}}</li>
  </ul>
</div>

</template>

<script>

export default {
  name: 'coin-card',
  props: ['coinTickers'],
}


</script>

<style lang="css" scoped>
</style>
