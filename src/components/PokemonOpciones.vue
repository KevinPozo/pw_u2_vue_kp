<template>
    <div class="opciones-container">
        <ul>
            <li @click="$emit('seleccionado', pokemon.id)" v-for="pokemon in listaPokemon" :key="pokemon.id" :class="{
                correcta: idSeleccionado && pokemon.id === idCorrecto,
                incorrecta: idSeleccionado && pokemon.id === idSeleccionado && pokemon.id !== idCorrecto
            }">
                {{ pokemon.nombre }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        listaPokemon: {
            type: Array,
            required: true
        },
        idCorrecto: {
            type: Number
        },
        idSeleccionado: {
            type: Number,
            default: null
        }
    }
}
</script>

<style>
ul {
    list-style-type: none;

}

li {
    background: white;
    border-radius: 5px;
    border: 1px solid black;
    cursor: pointer;
    width: 250px;
    margin-top: 15px;
    text-align: center;
    padding: 10px;
}

.correcta {
    background-color: #a5d6a7;
    border: 1px solid #2e7d32;
}

.incorrecta {
    background-color: #ef9a9a;
    border: 1px solid #c62828;
}
</style>