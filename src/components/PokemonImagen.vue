<template>
    <div class="pokemon-container">
        <img :src="srcImagen" alt="No se puede renderizar">

    </div>
</template>

<script>
export default {
    props: {
        pokemonId: {
            type: Number,
            required: true
        }
    },
    computed: {
        srcImagen() {
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
        }
    }
}
</script>

<style>
img {
    height: 200px;
    display: block;
    margin: 0 auto;
    box-shadow: 8px 4px 5px black;
    border: 2px solid black;
    border-radius: 15px;
}

.opciones-container {
    display: flex;
    justify-content: center;
    height: 200px;
}
</style>