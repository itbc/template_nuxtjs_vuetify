<template>
  <div>
    <div>
      <h1>Vue.js</h1>
      Hello {{ message }} !

      <v-btn
        icon
        @click="update"
      >
        <v-icon>mdi-minus</v-icon>
      </v-btn>
    </div>
    <br>
    <br>
    <select v-model="selected" multiple>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>
    <br>
    <br>
    <span>Selected: {{ selected }}</span>
    <br>
    <br>
    <span>Multiline message is:</span>
    <p style="white-space: pre-line;">{{ textmessage }}</p>
    <textarea v-model="textmessage" placeholder="add multiple lines"></textarea>
    <br>
    <br>
    <br>
    <br>
    <h5>Bitcoin Price Index</h5>
    <div v-for="currency in info" v-bind:key="currency" class="currency">
      {{ currency.description }}:
      <span class="lighten">
        <span v-html="currency.symbol"></span>
        {{ currency.rate_float | currencydecimal }}
        </span>
    </div>
    <br>
    <br>
    <div>
      {{ info }}
    </div>
    <br>
    <br>
    <br>
    <br>
    <div id="todo-list-example">
      <form v-on:submit.prevent="addNewTodo">
        <label for="new-todo">Add a todo</label>
        <input
          v-model="newTodoText"
          id="new-todo"
          placeholder="E.g. Feed the cat"
        >
        <button>Add</button>
      </form>
      <ul>
        <li
          is="todo-item"
          v-for="(todo, index) in todos"
          v-bind:key="todo.id"
          v-bind:title="todo.title"
          v-on:remove="todos.splice(index, 1)"
        ></li>
      </ul>
    </div>
  </div>
</template>
<script>
const axios = require('axios').default
export default {
  data () {
    return {
      message: 'World',
      selected: 'A',
      textmessage: 'World',
      newTodoText: '',
      info: '',
      todos: [
        {
          id: 1,
          title: 'Do the dishes'
        },
        {
          id: 2,
          title: 'Take out the trash'
        },
        {
          id: 3,
          title: 'Mow the lawn'
        }
      ],
      nextTodoId: 4
    }
  },
  mounted () {
    axios
      .get('sample###https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response.data.bpi))
  },
  filters: {
    currencydecimal (value) {
      return value.toFixed(2)
    }
  },
  methods: {
    update () {
      this.message = 'Vue.js'
    }
  },
  options: [
    { text: 'One', value: 'A' },
    { text: 'Two', value: 'B' },
    { text: 'Three', value: 'C' }
  ],
  addNewTodo () {
    this.todos.push({
      id: this.nextTodoId++,
      title: this.newTodoText
    })
    this.newTodoText = ''
  }
}
</script>
