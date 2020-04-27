<template>
<div>
    <v-container class="pa-2 grey lighten-5 large">
      <v-row>
        <v-col
        >
          <v-card
            class="pa-2 container_small"
          >
            <h1>LineChart1
              <v-btn outlined @click="fillData1()">
                Random
              </v-btn>
            </h1>
            <line-chart :chart-data="datacollection1" />
          </v-card>
        </v-col>
        <v-col
        >
          <v-card
            class="pa-2 container_small"
          >
            <h1>LineChart2
              <v-btn outlined @click="fillData2()">
                Push
              </v-btn>
            </h1>
            <line-chart :chart-data="datacollection2" />
          </v-card>
        </v-col>
        <v-col
        >
          <v-card
            class="pa-2 container_small"
          >
            <h1>LineChart3
              <v-btn outlined @click="fillData3()">
                Push
              </v-btn>
            </h1>
            <line-chart :chart-data="datacollection3" />
          </v-card>
        </v-col>
      </v-row>
      <v-row>
        <v-col
        >
          <v-card
            class="pa-2 container_small"
          >
            <h1>LineChart4
              <v-btn outlined @click="fillData4()">
                Push
              </v-btn>
            </h1>
            <line-chart :chart-data="datacollection4" />
          </v-card>
        </v-col>
        <v-col
        >
          <v-card
            class="pa-2 container_small"
          >
            <h1>LineChart5
              <v-btn outlined @click="fillData5()">
                Randomize
              </v-btn>
            </h1>
            <line-chart :chart-data="datacollection5" />
          </v-card>
        </v-col>
        <v-col
        >
          <v-card
            class="pa-2 container_small"
          >
            <h1>Increase
              <v-btn outlined @click="increase()">
                Increase height
              </v-btn>
            </h1>
            <line-chart :styles="myStyles"/>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
</div>
</template>
<script>
import LineChart from './chart/LineChart.js'
export default {
  components: {
    LineChart
  },
  data () {
    return {
      datacollection1: null,
      datacollection2: null,
      datacollection3: null,
      datacollection4: null,
      height: 100
    }
  },
  mounted () {
    this.fillData1()
    this.fillData2()
  },
  methods: {
    fillData1 () {
      this.datacollection1 = {
        labels: [this.getRandomInt(), this.getRandomInt()],
        datasets: [
          {
            label: 'Data One',
            backgroundColor: '#f87979',
            data: [this.getRandomInt(), this.getRandomInt()]
          }, {
            label: 'Data Two',
            backgroundColor: '#1177ff',
            data: [this.getRandomInt(), this.getRandomInt()]
          }
        ]
      }
    },
    fillData2 () {
      this.datacollection2 = {
        labels: [this.getRandomInt(), this.getRandomInt()],
        datasets: [
          {
            label: 'Data One',
            backgroundColor: '#f87979',
            data: [this.getRandomInt(), this.getRandomInt()]
          }, {
            label: 'Data Two',
            backgroundColor: '#1177ff',
            data: [this.getRandomInt(), this.getRandomInt()]
          }
        ]
      }
    },
    fillData3 () {
      this.datacollection3 = {
        labels: [this.getRandomInt(), this.getRandomInt()],
        datasets: [
          {
            label: 'Data One',
            backgroundColor: '#f87979',
            data: [this.getRandomInt(), this.getRandomInt()]
          }, {
            label: 'Data Two',
            backgroundColor: '#1177ff',
            data: [this.getRandomInt(), this.getRandomInt()]
          }
        ]
      }
    },
    fillData4 () {
      this.datacollection4 = {
        labels: [this.getRandomInt(), this.getRandomInt()],
        datasets: [
          {
            label: 'Data One',
            backgroundColor: '#f87979',
            data: [this.getRandomInt(), this.getRandomInt()]
          }, {
            label: 'Data Two',
            backgroundColor: '#1177ff',
            data: [this.getRandomInt(), this.getRandomInt()]
          }
        ]
      }
    },
    getRandomInt () {
      return Math.floor(Math.random() * (50 - 5 + 1)) + 5
    },
    increase () {
      this.height += 10
    }
  },
  computed: {
    myStyles () {
      return {
        height: `${this.height}px`,
        position: 'relative'
      }
    }
  }
}
</script>

<style>
  .container_small {
    max-width: 350px;
    margin:  10px auto;
  }
</style>
