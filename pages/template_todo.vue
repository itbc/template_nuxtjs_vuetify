<template>
  <div class="col-6 col-md-4 border border-info">
    No.29: Vue
    <hr>
    <div id="app-29">
        <h5>ToDoリスト</h5>
        <label v-for="label in options" :key="label">
          <input
            type="radio"
            v-model="current"
            v-bind:value="label.value">{{ label.label }}
        </label>
        （{{ computedTodos.length }} 件を表示）
        <table>
          <thead v-pre>
            <tr>
              <th class="id">ID</th>
              <th class="comment">コメント</th>
              <th class="state">状態</th>
              <th class="button">-</th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="item in computedTodos"
              v-bind:key="item.id"
              v-bind:class="{done:item.state}">
              <th>{{ item.id }}</th>
              <td>{{ item.comment }}</td>
              <td class="state">
                <button v-on:click="doChangeState(item)" class="btn btn-primary" >
                  {{ labels[item.state] }}
                </button>
              </td>
              <td class="button btn btn-primary" >
                <button v-on:click="doRemove(item)" >
                <!-- <button v-on:click.ctrl="doRemove(item)"> -->
                  削除
                </button>
              </td>
            </tr>
          </tbody>
        </table>
        <p>※削除ボタンはコントロールキーを押しながらクリックして下さい</p>
        <h5>新しい作業の追加</h5>
        <form class="add-form" v-on:submit.prevent="doAdd">
          コメント <input style="background-color: #f7f7f7" type="text" ref="comment">
          <button type="submit" class="btn btn-primary" >追加</button>
        </form>
      </div>
      <br>
  </div>
</template>
<script>
const STORAGE_KEY = 'todos-vuejs-demo'
const todoStorage = {
  fetch () {
    const todos = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]')
    todos.forEach(function (todo, index) {
      todo.id = index
    })
    todoStorage.uid = todos.length
    return todos
  },
  save (todos) {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(todos))
  }
}

export default {
  // components: {
  //   GChart
  // },
  data () {
    return {
      todos: [],
      // ★STEP11 抽出しているToDoの状態
      current: -1,
      options: [
        { value: -1, label: 'すべて' },
        { value: 0, label: '作業' },
        { value: 1, label: '完了' }
      ]
    }
  },
  computed: {
    computedTodos () {
      return this.todos.filter(function (el) {
        return this.current < 0 ? true : this.current === el.state
      }, this)
    },
    labels () {
      return this.options.reduce(function (a, b) {
        return Object.assign(a, { [b.value]: b.label })
      }, {})
    }
  },
  watch: {
    todos: {
      handler (todos) {
        todoStorage.save(todos)
      },
      // deep オプションでネストしているデータも監視できる
      deep: true
    }
  },
  created () {
    this.todos = todoStorage.fetch()
  },
  methods: {
    doAdd (event, value) {
      const comment = this.$refs.comment
      if (!comment.value.length) {
        return
      }
      this.todos.push({
        id: todoStorage.uid++,
        comment: comment.value,
        state: 0
      })
      comment.value = ''
    },
    doChangeState (item) {
      item.state = !item.state ? 1 : 0
    },
    doRemove (item) {
      const index = this.todos.indexOf(item)
      this.todos.splice(index, 1)
    }
  }
}
</script>
