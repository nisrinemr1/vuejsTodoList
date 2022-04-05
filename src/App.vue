<template>
  <div id="app">
    <todo-list/>
  </div>
</template>

<script>
import todoList from './components/todo.vue'

export default {
  components: { todoList },
  name: 'App'
}
</script>

<style>

  body{
    margin: 0;
    background-color: #ffe5eb;
    font-family: Avenir, Helvetica, Arial, sans-serif;
  }

  h1, h2, p {
    margin: 0;
  }

</style>
