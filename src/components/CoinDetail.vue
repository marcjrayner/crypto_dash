<!-- <template lang="html">
  <div v-if='coin'>
    <p v-overlay>Hello</p>
  </div>

</template>

<script>
export default {
  props: ['coin']
}
</script>

<style lang="css" scoped>
</style> -->

<template>
  <div v-if='coin'>
    <transition name="modal">
      <div v-if="isOpen">
        <div class="overlay" @click.self="isOpen = false;">
          <div class="modal">
            <img v-if='coin':src="logoURL" alt="">
            <h1>{{this.coin.name}}</h1>
            <ul>
              <li>Rank: {{this.coin.rank}}</li>
              <hr align="left" width="60%">
              <li>BTC: {{this.coin.price_btc}}</li>

              <li>USD: {{this.coin.price_usd}}</li>
              <hr align="left" width="60%">
              <li>24hr Volume: {{this.coin.volume24a}}</li>

              <li>Market Capitalization (USD): {{this.coin.market_cap_usd}}</li>
              <li>Total Supply: {{this.coin.tsupply}}</li>
              <hr align="left" width="60%">
              <li>Percent Change 1h: {{this.coin.percent_change_1h}}%</li>

              <li>Percent Change 24h: {{this.coin.percent_change_24h}}%</li>

              <li>Percent Change 7d: {{this.coin.percent_change_7d}}%</li>
              <hr align="left" width="60%">
            </ul>
            <GChart
            type="ColumnChart"
            :data="chartData"
            :options="chartOptions"
            />

          </div>
        </div>
      </div>
    </transition>
    <button @click="isOpen = !isOpen;">
      More info
    </button>
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  props: ['coin'],
  data() {
    return {
      isOpen: false,
      logoURL: 'https://raw.githubusercontent.com/rainner/binance-watch/master/public/images/icons/' + this.coin.symbol.toLowerCase() + '_.png',
      chartData: [
        ['Year', 'Sales', 'Expenses', 'Profit'],
        ['2014', 1000, 400, 200],
        ['2015', 1170, 460, 250],
        ['2016', 660, 1120, 300],
        ['2017', 1030, 540, 350]
      ],
      chartOptions: {
        chart: {
          title: 'Company Performance',
          subtitle: 'Sales, Expenses, and Profit: 2014-2017',
        }
      },
  components: {
    GChart
      }
    }
  }
}

</script>

<style scoped>
.modal {
  width: 700px;
  margin: 0px auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px 3px;
  transition: all 0.2s ease-in;
  /* font-family: Helvetica, Arial, sans-serif; */
}
.fadeIn-enter {
  opacity: 0;
}

.fadeIn-leave-active {
  opacity: 0;
  transition: all 0.2s step-end;
}

.fadeIn-enter .modal,
.fadeIn-leave-active.modal {
  transform: scale(1.1);
}
button {
  padding: 10px;
  border-radius: 10px;
  margin-top: 5px;
  background-color: dodgerblue;
  color: white;
  font-size: 1.1rem;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: #00000094;
  z-index: 999;
  transition: opacity 0.2s ease;
}
ul {
  list-style-type: none;
  text-align: left;
  /* position: absolute; */
  /* left: 700px;
  width: 700px; */
  /* display: flex;
  flex-direction: column;
  justify-content: flex-start; */
}
li {
  text-align: left;
}

</style>
