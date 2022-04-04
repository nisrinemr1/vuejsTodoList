<template>
  <div id="app">
    <todo-list/>
  </div>
</template>

<script>
import todoList from './components/todoList.vue'

export default {
  components: { todoList },
  name: 'App'
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
html{
  background-color: #ffe5eb;
}
</style>
