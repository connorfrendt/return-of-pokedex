<template>
  <div id="app">
    <Header
      v-bind:sort="sort"
      v-bind:filter="filter"
      v-bind:types="pokemonTypes"/>

    <Pokedex v-bind:pokemons="sortedPokemons"/>
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
        minAttack: '',
      },
      sort: {
        field: 'name',
        direction: 1
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
      return types;
    },
    filteredPokemons() {
      return this.pokemons.filter(pokemon => {
        const hasType = !this.filter.type || pokemon.type_1.includes(this.filter.type);
        const hasName = !this.filter.name || pokemon.pokemon.includes(this.filter.name);
        const hasMinAttack = !this.filter.minAttack || pokemon.attack >= this.filter.minAttack;
        return hasType && hasName && hasMinAttack;
      });
    },
    sortedPokemons() {
      const field = this.sort.field;
      const direction = this.sort.direction;

      return this.filteredPokemons.slice().sort((a, b) => {
        if(a[field] > b[field]) {
          return 1 * direction;
        }
        if(a[field] < b[field]) {
          return -1 * direction;
        }

        return 0;
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