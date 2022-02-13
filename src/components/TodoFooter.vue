<template>
   <li class="list-group-item d-flex justify-content-between">
       <span role="button">{{contarActivos}} Activos</span>
       <span role="button" @click="eliminarCompletados">ELIMINAR COMPLETADOS</span>
   </li>
</template>

<script>
import { computed, inject } from '@vue/runtime-core'
export default {
    setup() {
        const todos = inject('todos')


        const contarActivos = computed(()=> todos.value.filter(item => item.estado === false).length);
        const eliminarCompletados = ()=> todos.value = todos.value.filter(item => item.estado === false)
    return{contarActivos, eliminarCompletados}
    }

}
</script>

<style>
span{
    color: rgba(0, 0, 0, 0.651);
}
</style>