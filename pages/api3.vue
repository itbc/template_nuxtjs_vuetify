<template>
<v-app>
  <div class="Main">
    <v-container>
      <v-row class="mb-5">
      <v-col cols="12" sm="6" md="4">
      <v-text-field
          label="Title"
          v-model="titlename"
          height=12
          background="light-blue"
          outlined
          dense
        ></v-text-field>
      <!-- <input v-model="titlename" placeholder="search title"> -->
      <!-- <input style="background-color: #f7f7f7" type="text" ref="comment"> -->
      </v-col>
      <v-col cols="12" sm="6" md="5">
        <v-btn color="primary" @click="searchTitle()">Search</v-btn>
        <p v-show="errorFlag">サーバとの通信にエラーが発生しています</p>
      </v-col>
      </v-row>
      <v-row class="mb-5" style="height: 450px; overflow-y: scroll;">
      <v-col cols="12" sm="8" md="8">
    <!-- <ul>
      <v-list v-for="result in results" :key="result">{{ result.id }}: {{ result.title }}: {{ result.created_at }}: {{ result.likes_count }}</v-list>
    </ul> -->
    <v-simple-table
        :dense="dense"
        :fixed-header="fixedHeader"
        :height="height"
      >
    <!-- <v-simple-table dense border="1" loading loading-text="Loading... Please wait"> -->
      <template v-slot:default>
      <thead>
      <tr>
        <th v-for="column in columns" :key="column">{{ column }}</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="result in results" :key="result">
        <td>{{ result.id }}</td>
        <td>{{ result.title }}</td>
        <td>{{ result.created_at }}</td>
        <td>{{ result.likes_count }}</td>
      </tr>
      </tbody>
      </template>
    </v-simple-table>
      </v-col>
      <v-col cols="12" sm="8" md="4">

        <div id="contents">
          <GChart
            type="ColumnChart"
            :data="chart_data"
            :options="chartOptions"
          />
        </div>
      </v-col>
      </v-row>
    </v-container>
  </div>
</v-app>
</template>

<script>
import axios from 'axios'
import { GChart } from 'vue-google-charts'
export default {
  components: {
    GChart
  },
  data () {
    return {
      urlname: 'https://qiita.com/api/v2/items?query=',
      titlename: 'elixir',
      columns: [ "Id", "Title", "Created", "Likes" ],
      results: [],
      errorFlag: false,
      chartData: [
        ['Id', 'Title', 'Created', 'Likes'],
        ['2014', 1000, 400, 200],
        ['2015', 1170, 460, 250],
        ['2016', 660, 1120, 300],
        ['2017', 1030, 540, 350]
      ],
      chartOptions: {
        title: 'Qiita',
        subtitle: 'Title Name'
      },
      chart_data: [
        ['Title', 'Like']
      ]
      // chart_data: [
      //   ['Title', 'Like'],
      //   ['A', 300],
      //   ['B', 777],
      //   ['C', 1000]
      // ]
    }
  },
  // mounted: function(){
  //   axios.get('https://qiita.com/api/v2/items?query=elixir')
  //     .then(response => this.results = response.data)
  //     .catch(response => console.log(response))
  //     .catch(response =>{
  //       console.log(response)
  //       this.errorFlag = true;
  //     })
  // },
  methods: {
  searchTitle () {
    // axios.get('https://qiita.com/api/v2/items?query=elixir')
    axios.get(this.urlname + this.titlename)
      .then(response => this.results = response.data)
      .catch(response => console.log(response))
      .catch(response =>{
        console.log(response)
        this.errorFlag = true;
      })
    }
  }
}
</script>
