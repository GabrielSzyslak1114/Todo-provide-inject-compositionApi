<template>
      <div class="card mt-3 ">
          <div class="card-body d-flex justify-content-between">
              <span role="button" @click="filtrar('active')">Activos</span>
              <span role="button" @click="filtrar('all')">Todos</span>
              <span role="button" @click="filtrar('completed')">Completadas</span>
          </div>
      </div>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
    setup(){
        const estado = inject('estadoTodos')
        const filtrar = valor => estado.value = valor
        return{estado, filtrar}
    }
}
</script>

<style>

</style>