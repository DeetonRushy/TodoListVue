<template>
  <title>Todo List</title>
  <Banner title="Deetons Todolist" />
  <TodoList msg="Welcome to Your Vue.js App"/>
</template>

<script>
import TodoList from './components/TodoList.vue'
import Banner from './components/Banner.vue'

export default {
  name: 'App',
  components: {
      TodoList,
      Banner
  }
}
</script>

<style>
html {
    background-color: #656565
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
