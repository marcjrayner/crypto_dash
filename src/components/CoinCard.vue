<template lang="html">
  <div class="card">
    <div class="logo">
      <img :src="logoURL" alt="">
    </div>
    <li>NAME: {{ticker.name}} RANK {{ticker.rank}}</li>
  </div>


</template>

<script>
export default {
  name: 'coin-card',
  data() {
    return {
      logoURL: 'https://raw.githubusercontent.com/rainner/binance-watch/master/public/images/icons/' + this.ticker.symbol.toLowerCase() + '_.png'
    }
  },
  props: ['ticker']
}
</script>

<style lang="css" scoped>
.card {
  background: #eee;
  padding: 10px 20px;
  margin: 20px 20px;
  width: 20%;
  display: flex;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}
</style>
