<template>
  <div>
    <h1>Lista de tareas</h1>
    <router-link :to="{name: 'agregar'}">
      <button class="btn btn-success btn-block">Agregar</button>
    </router-link>
    <ul class="list-group mt-5">
      <li v-for="item of tareas" :key="item.id" class="list-group-item">
        {{item.id}} - {{item.nombre}}
        <div class="float-right">
          <router-link :to="{name:'editar', params:{id: item.id}}">
            <button class="btn btn-warning btn-sm mr-2" @click="getTareas(id)">Editar</button>
          </router-link>
          <button @click="eliminarTarea(item.id)" class="btn btn-danger btn-sm">Eliminar</button>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
import { mapActions, mapState } from "vuex";

export default {
  name: "Inicio",
  methods: {
    ...mapActions(["getTareas", "eliminarTarea"])
  },
  created() {
    this.getTareas();
  },
  computed: {
    ...mapState(["tareas"])
  }
};
</script>
