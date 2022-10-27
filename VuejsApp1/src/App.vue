<template>
  <RouterView>
    <Banner title="Deetons Todolist" />
    <TodoList msg="Welcome to Your Vue.js App"/>
  </RouterView>
</template>

<script>
import TodoList from './components/TodoList.vue'
import Banner from './components/Banner.vue'

import RouterView from 'vue-router';

export default {
  name: 'App',
  components: {
      TodoList,
      Banner,
      RouterView
  }
}
</script>

<style>
html{
  background-color: #212121;
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
