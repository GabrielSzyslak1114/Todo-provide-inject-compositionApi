<template>
<h3>Todos</h3>
  <todo-form/>
  <todo-list/>
  
</template>

<script>
import { ref } from '@vue/reactivity'
import TodoForm from './TodoForm.vue'
import { provide } from '@vue/runtime-core'
import {watchEffect} from 'vue' 
import TodoList from './TodoList.vue'
export default {
  components: { TodoForm, TodoList },
  setup(){

      const todos = ref([])
      provide('todos', todos)

      if (localStorage.getItem('todos')) {
        todos.value = JSON.parse(localStorage.getItem('todos'))
      }
      watchEffect(()=>{
          localStorage.setItem('todos', JSON.stringify(todos.value))
      })
  }

}
</script>

<style scoped>
h3{
  color: #fcfcfc;
}
</style>