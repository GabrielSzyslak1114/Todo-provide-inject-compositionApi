<template>
    <ul class="list-group">
       <todo-item v-for="todo in todos" :key="todo.id" :todo="todo"/>
       <li v-if="todos.length === 0" class="list-group-item">No hay elementos</li>
       <todo-footer v-if="todos.length !== 0"/>
       <todo-filter v-if="todos.length !== 0"/>
    </ul>
</template>

<script>
import { computed, inject, provide, ref } from '@vue/runtime-core'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFilter from './TodoFilter.vue'
export default {
  components: { TodoItem, TodoFooter, TodoFilter },
    setup(){
        const todosTodos = inject('todos')

        const estado = ref('all')
        
        const todos = computed(()=> {
            if(estado.value === 'all'){
                return todosTodos.value
            }
            if(estado.value === 'active'){
                return todosTodos.value.filter(item => item.estado === false)
            }
            if(estado.value === 'completed'){
                return todosTodos.value.filter(item => item.estado === true)
            }
        })
        provide('estadoTodos', estado)
        return{todos}
    }
}
</script>

<style>

</style>