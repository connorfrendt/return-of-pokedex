<template>
  <div id="app">
    <Header
      v-bind:sort="sort"
      v-bind:filter="filter"
      v-bind:types="pokemonTypes"/>

    <Pokedex v-bind:pokedex="pokedex"/>
  </div>
</template>

<script>
import pokedexApi from './services/pokedex-api.js';
import Pokedex from './components/Pokedex.vue';
import Header from './components/Header.vue';

export default {
  data() {
    return {
      pokedex: pokedexApi.getPokedex(),
      filter: {
        pokemon: '',
        type: '',
        attack: 0,
        defense: 0,
      },
      sort: {
        field: 'pokemon',
        direction: 1
      }
    }
  },
  components: {
    Header,
    Pokedex
  },
  computed: {
    pokemonTypes() {
      const types = [];
      this.pokedex.forEach(pokemon => {
        if(!types.includes(pokemon.type_1)) {
          types.push(pokemon.type_1);
        }
      });
      return types;
    },
    filteredPokemon() {
      return this.pokedex.filter(pokemon => {
        const hasAttack = !this.filter.attack || pokemon.attack >= this.filter.attack;
        return hasAttack;
      });
    }
  }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
