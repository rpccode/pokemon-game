<template>
    <div class="pokemon-container">
        <img class="hidden-pokemon" alt="pokemon" :src="imgSrc">
        <img alt="pokemon" :src="imgSrc" class="fade-in" v-if="showPokemon">

    </div>

</template>

<script>
    export default {
        props:{
            pokemonId:{
                type: Number,
                required:true
            },
            showPokemon:{
                type: Boolean,
                required:true,
                defauld: false
            }
        },
        computed:{
            imgSrc(){
                return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
            }
        }
    }
</script>

<style  scoped>
/* Pokemon Picture */
.pokemon-container {
    height: 200px;
    display: flex;
    justify-content: center;
}

img {
    height: 200px;
    position: absolute;
    /* right: 32%; */
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
}

.hidden-pokemon {
    filter: brightness(0);
}

/* Pokemon Options */
ul {
    list-style-type: none;
}

li {
    background-color: white;
    border-radius: 5px;
    border: 1px solid rgba(0, 0, 0, 0.2);
    cursor: pointer;
    margin-bottom: 10px;
    width: 250px;
}

li:hover {
    background-color: rgba(0, 0, 0, 0.05);
}

.options-container {
    display: flex;
    justify-content: center;
}
</style>