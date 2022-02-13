<template>
  <form @submit.prevent="formulario">
      <input v-model.trim="texto" type="text" placeholder="ingresar tarea..." class="form-control my-3">
  </form>
</template>

<script>
import { inject, ref } from '@vue/runtime-core'
export default {
    setup(){
        const todos = inject('todos');
        //Texto esta conectado al V-MODEL DEL FORMULARIO
        const texto = ref('');

        const formulario = () =>{
            if(texto.value === ''){
                console.log('input vacio')
                return 
            }
            const todo = {
                texto: texto.value,
                estado: false,
                id: Date.now()
            }

            todos.value.push(todo)
            texto.value = '';
            console.log(todos)
        }
 
        return{formulario, texto}
  }
}
</script>

<style>

</style>