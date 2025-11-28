<!--Elemento: Template HTML Script: JS Style: todo lo de CSS-->
<template>
  <div>
    <h1>{{ tit }}</h1>

    <p>{{ inicio }}<sup>2</sup> = {{ obtenerCuadrado() }}</p>
    <p>{{ inicio }}<sup>3</sup> = {{ calcularCubo }}</p>
    <p>{{ inicio }}<sup>2</sup> = {{ calcularCuadrado }}</p>
    <p>{{ inicio }}<sup>3</sup> = {{ obtenerCubo() }}</p>

    <div>
      <button @:click="incrementar()">+1</button>
      <button @:click="decrementar()">-1</button>
      <button v-show="mostrar">Prueba</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero: this.inicio,
      titulo: "Contador",
    };
  },
  methods: {
    obtenerCuadrado() {
      console.log(this.tit);
      return this.numero * this.numero;
    },
    obtenerCubo() {
      return this.numero * this.numero * this.numero;
    },
    incrementar() {
      this.numero++;
    },
    decrementar() {
      this.numero--;
    },
  },
  computed: {
    calcularCuadrado() {
      console.log("Entro a propiedad computada");
      return this.numero * this.numero;
    },
    calcularCubo() {
      return this.numero * this.numero * this.numero;
    },
  },
  /*props: ["tit", "inicio", "mostrar"], Declaracion básica de props*/
  props: {
    tit: String,
    inicio: {
      type: Number,
      default: 99,
      validator(value) {
        return value > 10;
      },
    },
    mostrar: Boolean,
  },
  /*Algunos tipos de props:
  String, number, boolean,array, object,Date,Function, Big*/
};
</script>

<style></style>
