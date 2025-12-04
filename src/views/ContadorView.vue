<template>
  <div>
    <contador tit="Contador 1" :inicio="12 + 4" :mostrar="true" />
    <contador tit="Contador 2" :inicio="20" :mostrar="false" />
  </div>
</template>

<script>
import Contador from "../components/Contador.vue";
export default {
  components: {
    Contador,
  },
};
</script>

<style></style>
