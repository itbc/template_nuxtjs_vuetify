<template>
<v-app>
  <div class="Main">
    <v-container>
      <v-row class="mb-5">
				<!-- <v-col cols="12" sm="6" md="2">
					<v-text-field
						label="Title"
						v-model="section"
						height=12
						background="light-blue"
						outlined
						dense
					></v-text-field>
				</v-col> -->

				<select v-model="section">
					<option v-for="section in sections" :v-model="section" :key="section">{{ section }}</option>
				</select>

				<v-col cols="12" sm="6" md="5">
					<v-btn color="primary" @click="getPosts(section)">Search</v-btn>
				</v-col>
      </v-row>
      <v-row class="mb-5" style="height: 450px; overflow-y: scroll;">
				<h3 v-if="!loading">{{ title }}</h3>
				<div v-if="loading" class="loader">
					<img src="http://cdnjs.cloudflare.com/ajax/libs/semantic-ui/0.16.1/images/loader-large.gif" alt="loader">
				</div>
				<div v-if="!loading" :results="results">
					<!-- <news-list v-if="!loading" :results="results"></news-list> -->
				</div>

				<v-simple-table>
					<template v-slot:default>
					<tbody>
					<tr v-for="post in posts" :key="post">
						<td>{{ post.title }}</td>
						<td>{{ post.abstract }}</td>
					</tr>
					</tbody>
					</template>
				</v-simple-table>
      </v-row>
    </v-container>
  </div>
</v-app>
</template>

<script>
import axios from 'axios'
const NYTBaseUrl = 'https://api.nytimes.com/svc/topstories/v2/'
const ApiKey = 'easxAGMRM5PDlksmuh1IZLOiQRvGrtRA'
const SECTIONS = "home, arts, automobiles, books, business, fashion, food, health, insider, magazine, movies, national, nyregion, obituaries, opinion, politics, realestate, science, sports, sundayreview, technology, theater, tmagazine, travel, upshot, world"
export default {
  data () {
    return {
			// url: NYTBaseUrl + 'home' + '.json?api-key=' + ApiKey,
			results: [],
			posts: [],
			sections: SECTIONS.split(', '),
			section: 'home', 
			loading: true,
			title: '',
    }
  },
  methods: {
  // searchTitle () {
  //   axios.get(this.url)
  //     .then(response => this.posts = response.data.results)
  //     .catch(response => console.log(response))
  //     .catch(response =>{
  //       console.log(response)
  //       this.errorFlag = true;
  //     })
  //   }
	// }

		// buildUrl: function (url) {
		// 		return NYTBaseUrl + url + ".json?api-key=" + ApiKey;
		// },

		getPosts: function (section) {
      let url = NYTBaseUrl + section + ".json?api-key=" + ApiKey;
      axios.get(url).then((response) => {
        this.loading = false;
        this.results = response.data.results;
        let title = this.section !== 'home' ? "Top stories in '"+ this.section + "' today" : "Top stories today";
				this.title = title + "(" + response.data.num_results+ ")";
				this.posts = this.results; //temporary added
      }).catch((error) => { console.log(error); });
		}
	}
}
</script>
