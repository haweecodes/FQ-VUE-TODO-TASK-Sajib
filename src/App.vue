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
@import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');

body{
  background-color: black;
  font-family: 'Roboto', sans-serif;
}
</style>
