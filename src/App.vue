<template>
  <div id="app">
  <div class="container">
    <h2 class="text-center">Todo Apllication</h2>
    <div class="mb-3">
      <label for="basic-url" class="form-label">Your Todo LIst</label>
      <div class="input-group">
    <input type="text" class="form-control" v-model="userInput">
    <span class="input-group-text"><button type="button" class="btn btn-primary" @click="fn_AddTodo">Add</button></span>
  </div>
  </div>
  <div class="list-group">
    <li class="list-group-item" v-for="( item, key ) in todoList" v-bind:key="key">
      {{ item.label }}
      <button type="button" class="btn btn-outline-danger" @click="fn_DeleteTodo(item.key)">delete</button>
    </li>
  </div>
  </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      userInput: '',
      todoList: []
    }
  },
  components: {
  },
  methods: {
    fn_AddTodo () {
      if (this.userInput === '') return
      this.todoList.push({
        key: this.todoList.length,
        label: this.userInput
      })
      this.userInput = ''
    },
    fn_DeleteTodo (key) {
      this.todoList = this.todoList.filter((item) => item.key !== key)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
