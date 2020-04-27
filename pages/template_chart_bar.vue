<template>
<div id="app">
  <v-app id="inspire">
    <v-container class="pa-2 grey lighten-5">
      <v-row>
        <v-col
        >
          <v-card
            class="pa-2"
          >
            <h1>Line + Random
              <v-btn outlined @click="renderChart()">
                Randomize
              </v-btn>
            </h1>
            <bar-chart :chartdata="chartData" :options="chartOptions"/>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</div>
</template>
<script>
import { Bar } from 'vue-chartjs'
export default {
  extends: Bar,
  data: () => ({
    chartdata: {
      labels: ['January', 'February'],
      datasets: [
        {
          label: 'Data One',
          backgroundColor: '#f87979',
          data: [40, 20]
        }
      ]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false
    }
  }),

  mounted () {
    this.renderChart(this.chartdata, this.options)
  }
}</script>

<style>
  .small {
    max-width: 400px;
    margin:  150px auto;
  }
</style>
