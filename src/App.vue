<template>
  <div id="app">
    <!-- <Header
      v-bind:sort="sort"
      v-bind:filter="filter"
      v-bind:types="pokemonTypes"/> -->

    <Pokedex v-bind:pokedex="pokedex"/>
  </div>
</template>

<script>
import pokedexApi from './services/pokedex-api.js';
import Pokedex from './components/Pokedex.vue';

export default {
  data() {
    return {
      pokedex: pokedexApi.getPokedex(),
    }
  },
  components: {
    Pokedex
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
