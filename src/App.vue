<template>
  <div>
    <ToDoList/>
  </div>
</template>

<script>
import ToDoList from './components/TodoList.vue'

export default {
  name: 'app',
  components: {
    ToDoList
  }
}
</script>

<style>
body{
  background-color: black;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
