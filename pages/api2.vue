<template>
  <div class="Main">
    <div>
      <v-col cols="12" sm="6" md="3">
        <v-text-field
          label="Outlined"
          v-model="name"
          outlined
        ></v-text-field>
        <!-- <input v-model="name"> -->
        <v-btn @click="createNewUser" color="primary">Create User</v-btn>
      </v-col>

    </div>
    <ul>
      <li v-for="user in users" :key="user.id">{{ user.name }}:<v-btn @click="deleteUser(user.id)" variant="secondry" class="ml-10">Delete</v-btn></li>
    </ul>
    <p v-show="errorFlag">サーバとの通信にエラーが発生しています</p>

  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      value: '',
      context: null,
      users: [],
      name: '',
      errorFlag: false
    }
  },
  methods: {
    onContext (ctx) {
      this.context = ctx
    },
    createNewUser: function(){
      axios.post('https://jsonplaceholder.typicode.com/users',{
        name: this.name
      })
      .then(response => this.users.unshift(response.data))
      .catch(response => console.log(response))     
    },
    deleteUser: function(id){
      axios.delete('https://jsonplaceholder.typicode.com/users/' + id)
          .then(response => console.log(response))
          .catch(response => console.log(response)) 
    },
  },
  mounted :function(){
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => this.users = response.data)
      .catch(response => console.log(response))
      .catch(response =>{
        console.log(response)
        this.errorFlag = true;
      })
    // axios.get('https://jsonplaceholder.typicode.com/users')
    //   .then(response => {
    //     console.log(response.data)
    //     console.log(response.status)
    //     console.log(response.headers)
    //     console.log(response.statusText)
    //     console.log(response.config)
    //   })
    //   .catch(response => console.log(response))
  }  
}
// const form = new FormData();
// form.append('file',event.dataTransfer.files[0]);
// axios.post('/api/karte_file',form,{
// 	onUploadProgress: progressEvent => {
// 		console.log(progressEvent.loaded)
// 		console.log(progressEvent.total)
// 	}
// });
// ratio = Math.floor((progressEvent.loaded)*100/progressEvent.total) + '%';
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  /* display: inline-block; */
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
