<template>
    <div>
        <PokemonImagen
            v-if="mostrarImagen && pokemonGanador"
            :pokemonId="pokemonGanador"
        />

        <PokemonOpciones
            :listaPokemon="pokemonaArr"
            :idCorrecto="pokemonGanador"
            :idSeleccionado="seleccionUsuario"
            @seleccionado="evaluarGanador($event)"
        />

        <div v-if="mensaje" class="mensaje-resultado">
            <h1>{{ mensaje }}</h1>
        </div>

        <button @click="destruirImagen">Destruir Imagen</button>
        <button @click="mostrarImagenMetodo">Mostrar Imagen</button>
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
            mostrarImagen: true,
            pokemonaArr: [],
            pokemonGanador: null,
            mensaje: null,
            seleccionUsuario: null
        }
    },
    beforeCreate() {
        console.log("beforeCreate: instancia creada");
    },
    created() {
        console.log("created: data y métodos inicializados");
    },
    beforeMount() {
        console.log("beforeMount: antes del primer render");
    },
    mounted() {
        console.log("mounted: componente montado");
        this.iniciarJuego();
    },
    beforeUpdate() {
        console.log("beforeUpdate: antes de re-render");
    },
    updated() {
        console.log("updated: después del re-render");
    },
    beforeUnmount() {
        console.log("beforeUnmount: justo antes de destruir el componente");
    },
    unmounted() {
        console.log("unmounted: componente destruido");
    },
    methods: {
        async iniciarJuego() {
            this.pokemonaArr = await obtenerVectorNumericoFacade();
            const idAleatorio = obtenerAleatorioFacade(0, 3);
            this.pokemonGanador = this.pokemonaArr[idAleatorio].id;
            this.mensaje = null;
            this.seleccionUsuario = null;
            this.mostrarImagen = true;
        },
        evaluarGanador(idGanador) {
            if (this.seleccionUsuario) return;

            this.seleccionUsuario = idGanador;

            if (idGanador === this.pokemonGanador) {
                this.mensaje = "Pokemon Correcto";
            } else {
                this.mensaje = "Pokemon Incorrecto";
            }

            setTimeout(() => {
                this.iniciarJuego();
            }, 2000);
        },
        destruirImagen() {
            this.mostrarImagen = false;
        },
        mostrarImagenMetodo() {
            this.mostrarImagen = true;
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
