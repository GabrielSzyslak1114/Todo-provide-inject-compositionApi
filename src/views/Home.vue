<template>
  <div class="container">
  <todo-app/>
  </div>
</template>

<script>
import TodoApp from '../components/TodoApp.vue'
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
    TodoApp
    
  }
}
</script>

<style scoped>
.container{
    height: 100vh;
    width: 100%;
    position: relative;
    display: grid;
    grid-template-rows: 80px 100px 500px;
    color: #fcfcfc;
    text-align: center;
    padding: 2%;
  
}
</style>