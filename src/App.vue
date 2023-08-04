<template>
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <pokemon-page/>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import PokemonPage from './page/PokemonPage.vue'

export default {
  name: 'App',
  components: {
    PokemonPage
    // HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
