<template>
  <div>
    <label for="id_nombre">Nombre: </label>
    <input type="text" id="id_nombre" v-model="nombre" />

    <label for="id_apellido">Apellido: </label>
    <input type="text" id="id_apellido" v-model="apellido" />

    <button @:click="imprimirNombre()">Imprimir nombre</button>
    <button @:click="imprimirApellido()">Imprimir Apellido</button>
    <button @:click="agregarEstudiante()">Agregar estudiante</button>

    <!--
    <ul>
      <li
        v-for="{ nombre, apellido } in arreglo"
        :key="nombre"
        v-show="nombre"
      >
        {{ nombre }} -- {{ apellido }}
      </li>
    </ul>
    -->

    <h2>Tabla</h2>

    <table border="1">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Apellido</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(est, index) in arreglo" :key="index" v-show="est.nombre">
          <td>{{ est.nombre }}</td>
          <td>{{ est.apellido }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: null,
      apellido: null,
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
      console.log(estudiante);
      this.arreglo.push(estudiante);
      this.limpiarFormulario();
    },
    limpiarFormulario() {
      this.nombre = null;
      this.apellido = null;
    },
  },
};
</script>

<style></style>
