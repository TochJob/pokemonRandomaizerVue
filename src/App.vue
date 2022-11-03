<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/exemple.png">
    <pokemon-generator/>
  </div>
</template>

<script>
import PokemonGenerator from './components/pokemonGenerator.vue'

export default {
  name: 'App',
  components: {
    PokemonGenerator
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
