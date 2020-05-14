<template>
  <div>
    No.30: Axios
    <hr>
    <div id="app-30">
      <h5>Price Index</h5>
      <v-btn
        v-on:click="checkPrice"
      >
        <v-icon>mdi-menu</v-icon>
      </v-btn>
      <v-btn
        v-on:click="clearPrice"
      >
        <v-icon>mdi-menu</v-icon>
      </v-btn>
      <div v-for="currency in info" class="currency" :key="currency">
        {{ currency.description }}:
        <span class="lighten">
          <span v-html="currency.symbol"></span>
          {{ currency.rate_float | currencydecimal }}
        </span>
      </div>
    </div>
  </div>
</template>
<script>
import { axios } from 'axios'
export default {
  data () {
    return {
      info: null
    }
  },
  methods: {
    checkPrice (event, value) {
      axios
        .get('https://api.coindesk.com/v1/bpi/currentprice.json')
        .then(response => (this.info = response.data.bpi))
    },
    clearPrice (event, value) {
      this.info = ''
      console.log('working now')
    }
  },
  filters: {
    currencydecimal (value) {
      return value.toFixed(2)
    }
  }
}
</script>
