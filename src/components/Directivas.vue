<template>
  <div>
    <label for="id_nombre">Nombre: </label>
    <input type="text" id="id_nombre" v-model="nombre" />

    <label for="id_apellido">Apellido: </label>
    <input type="text" id="id_apellido" v-model="apellido" />

    <button @click="imprimirNombre()">Imprimir nombre</button>
    <button @click="imprimirApellido()">Imprimir Apellido</button>
    <button @click="agregarEstudiante()">Agregar estudiante</button>

    <hr />

    <h2>Lista de estudiantes</h2>

    <label for="id_nombre_1">Nombre: </label>
    <input type="text" id="id_nombre_1" v-model="nombre1" />

    <label for="id_apellido_1">Apellido: </label>
    <input
      @keyup.enter="agregarEstudiante1"
      type="text"
      id="id_apellido_1"
      v-model="apellido1"
    />

    <ul>
      <li v-for="(est, index) in arreglo" :key="index" v-show="est.nombre">
        {{ est.nombre }} — {{ est.apellido }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: null,
      apellido: null,
      nombre1: null,
      apellido1: null,

      arreglo: [],
    };
  },
  methods: {
    imprimirNombre() {
      console.log(this.nombre);
    },
    imprimirApellido() {
      console.log(this.apellido);
    },
    agregarEstudiante() {
      const estudiante = {
        nombre: this.nombre,
        apellido: this.apellido,
      };
      this.arreglo.push(estudiante);
      this.limpiarFormulario();
    },

    agregarEstudiante1(event) {
      const estudiante = {
        nombre: this.nombre1,
        apellido: this.apellido1,
      };

      this.arreglo.push(estudiante);
      this.limpiarFormulario1();
    },

    limpiarFormulario() {
      this.nombre = null;
      this.apellido = null;
    },

    limpiarFormulario1() {
      this.nombre1 = null;
      this.apellido1 = null;
    },
  },
};
</script>

<style></style>
