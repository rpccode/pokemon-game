<template>
    <h1 v-if="!pokemon">Espere por favor.........</h1>
    <div v-else>
        <h1>¿Quién es ese Pokémon?</h1>
        <pokemon-picture :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
        <pokemon-options :pokemons="pokemonArr" @selection="checkAnswer"/>

        <templete v-if="showAnswer">
            <h2 class="fade-in">{{ message }}</h2>
            <button @click="newGame">
                Nuevo Juego
            </button>
        </templete>
    </div>
</template>

<script>
import PokemonPicture from '@/components/PokemonPicture.vue'
import PokemonOptions from '@/components/PokemonOptions.vue'
import getPokemonOptions  from "@/helpers/getPokemonOptions";
// console.log(getPokemonOptions())
export default {
  components: { PokemonPicture, PokemonOptions },
  data(){
    return{
        pokemonArr: [],
        pokemon:null,
        showPokemon: false,
        showAnswer: false,
        message:''
    }
  },
  methods: {
  async  mixPokemonArray(){
        this.pokemonArr = await getPokemonOptions()

        const rndInt =  Math.floor( Math.random() * 4)
        this.pokemon = this.pokemonArr[ rndInt ]
    },
    checkAnswer( pokemonId){
        this.showPokemon = true;
        this.showAnswer = true;

        if ( pokemonId === this.pokemon.id) {
            this.message = `Aceptaste, Es ${this.pokemon.name}`
        }else{
            this.message =`Oops, era ${this.pokemon.name}`
        }
    },
    newGame(){
        this.showAnswer =false;
        this.showPokemon =false;
        this.pokemonArr = [];
        this.pokemon = null;
        this.mixPokemonArray();
    }
  },
  mounted() {
    this.mixPokemonArray()
  },

}
</script>

<style lang="scss" scoped></style>