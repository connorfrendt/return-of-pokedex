<template>
  <div id="app">
    <Header
      v-bind:filter="filter"
      v-bind:types="pokemonTypes"
    />

    <Pokedex v-bind:pokemons="pokemons"/>
  </div>
</template>

<script>
import Pokedex from './components/Pokedex.vue';
import Header from './components/Header.vue';
import pokemons from './services/pokedex.js';

export default {
  data() {
    return {
      pokemons,
      filter: {
        name: '',
        type: '',
      }
    };
  },
  components: {
    Header,
    Pokedex
  },
  computed: {
    pokemonTypes() {
      const types = [];
      this.pokemons.forEach(pokemon => {
        if(!types.includes(pokemon.type_1)) {
          types.push(pokemon.type_1);
        }
      });
      // console.log(types);
      return types;
    },
    filteredPokemons() {
      return this.pokemons.filter(pokemon => {
        const hasName = !this.filter.name || pokemon.pokemon.includes(this.filter.name);
        return hasName;
      });
    }
  }
};

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