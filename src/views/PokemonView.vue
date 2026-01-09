<template>
    <PokemonImagen :pokemonId="pokemonGanador" />
    <PokemonOpciones :listaPokemon="pokemonaArr" :idCorrecto="pokemonGanador" :idSeleccionado="seleccionUsuario"
        @seleccionado="evaluarGanador($event)" />
    <div v-if="mensaje" class="mensaje-resultado">
        <h1>{{ mensaje }}</h1>
    </div>
</template>

<script>
import PokemonOpciones from '@/components/PokemonOpciones.vue';
import PokemonImagen from '@/components/PokemonImagen.vue';
import { obtenerVectorNumericoFacade, obtenerAleatorioFacade } from '../clients/PokemonClient';
export default {
    components: {
        PokemonOpciones,
        PokemonImagen
    },
    data() {
        return {
            pokemonaArr: [],
            pokemonGanador: null,
            mensaje: null,
            seleccionUsuario: null
        }
    },
    mounted() {
        this.iniciarJuego();
    },
    methods: {
        async iniciarJuego() {
            this.pokemonaArr = await obtenerVectorNumericoFacade();
            const idAleatorio = obtenerAleatorioFacade(0, 3);
            this.pokemonGanador = this.pokemonaArr[idAleatorio].id;
            this.mensaje = null;
            this.seleccionUsuario = null;
        },
        evaluarGanador(idGanador) {
            if (this.seleccionUsuario) return;
            this.seleccionUsuario = idGanador;
            if (idGanador == this.pokemonGanador) {
                this.mensaje = "Pokemon Correcto";
            } else {
                this.mensaje = "Pokemon Incorrecto";
            }
            setTimeout(() => {
                this.iniciarJuego();
            }, 2000);
        }

    }
}
</script>

<style>
.mensaje-resultado {
    border: 1px solid #ccc;
    padding: 20px;
    margin: 60px auto 20px auto;
    width: 300px;
    text-align: center;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    background-color: #f9f9f9;
}

.mensaje-resultado h1 {
    color: #2c3e50;
    margin: 0;
}


</style>