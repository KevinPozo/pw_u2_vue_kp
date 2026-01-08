<template>
    <PokemonImagen :pokemonId="pokemonId"/>
    <PokemonOpciones />
</template>

<script>
import PokemonOpciones from '@/components/PokemonOpciones.vue';
import PokemonImagen from '@/components/PokemonImagen.vue';
export default {
    components: {
        PokemonOpciones,
        PokemonImagen
    },
    data() {
        return {
            pokemonId: 123
        }
    }
}
</script>

<style></style>