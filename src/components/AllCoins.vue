<template lang="html">
  <select>
    <option v-for="(ticker, index) in coinTickers" :ticker="ticker" :key="index" >{{ticker.name}}</option>
  </select>
</template>

<script>
export default {
  name: 'all-coins',
  props:['coinTickers']

}
</script>

<style lang="css" scoped>
</style>
